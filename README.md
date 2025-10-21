VLM-Vac is a research simulation framework developed to model the behavior of a vacuum cleaner operating in a household environment.  
The simulation spans nine virtual days, following a three-day sequence each representing a randomly generated household scenario.  
The framework integrates vision–language models (VLMs) to generate semantic descriptions of the environment, produce language embeddings, and incorporate these into the training process for improved task performance and evaluation.

This repository accompanies the paper:

> "VLM-Vac: Enhancing Smart Vacuums Through VLM Knowledge Distillation and Language-Guided Experience Replay"
> 
> Reihaneh Mirjalili, Michael Krawez, Florian Walter, Wolfram Burgard — 2025

---
To generate the nine virtual days, download the VLM-Vac_dataset: !wget https://huggingface.co/datasets/rmirjalili/VLM-Vac-dataset/resolve/main/VLM-Vac-dataset.zip
Then run the notebook Language_description_generator/data_sorter.ipynb

Before running any experiments, language descriptions must be generated.  
This is achieved by executing the Jupyter notebook: Language_description_generator/language_descriptor.ipynb

This notebook performs the following steps:
1. Uses GPT to generate natural language descriptions for each image collected across the nine simulated days.  
2. Converts these descriptions into embeddings.  
3. Saves these two files: image_descriptions_dict.pickle , text_embeddings_dict.pickle

Finally, to run the main processing pipeline, run this notebook: main.ipynb

---

The results/ directory contains comprehensive performance data for multiple learning strategies:

- umulative Learning
- Language-Based Experience Replay (ER)
- Naive Fine-Tuning

After training, daily results are organized as follows:

results/language_based_ER/experience_buffer/dayX/
results/language_based_ER/vacuum_performance/dayX/

where X represents the day index (1–9). Additionally, the daily F1 scores are stored in the file daily_f1_scores.pkl.

The language description prompts have been updated to align with the most recent GPT-4o model, resulting in minor variations in the generated text and corresponding embeddings. Redundant images have been removed, and augmented variants have been introduced to enhance dataset quality and maintain sample diversity. As each virtual day is generated stochastically, numerical results may vary slightly from those reported in the original publication.

---

If you use VLM-Vac in your research or build upon it, please cite the following paper:

@inproceedings{mirjalili2025vlm,
  title={VLM-Vac: Enhancing Smart Vacuums Through VLM Knowledge Distillation and Language-Guided Experience Replay},
  author={Mirjalili, Reihaneh and Krawez, Michael and Walter, Florian and Burgard, Wolfram},
  booktitle={2025 IEEE International Conference on Robotics and Automation (ICRA)},
  year={2025},
}

