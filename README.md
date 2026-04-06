# ActAdd Efficacy and Concept Compositionality in Activation Steering
Our code and data for exploring concept steerability and compositionality in LLMs using Activation Addition (ActAdd).

## Experiments
Our experiments can be found at **[`concept_steerability.ipynb`](./concept_steerability.ipynb)** and **[`concept_compositionality.ipynb`](./concept_compositionality.ipynb)**.
 - **[`concept_steerability.ipynb`](./concept_steerability.ipynb)**: Includes code to calculate the optimal layer of each concept, along with code to evaluate each concept at its optimal layer.
 - **[`concept_compositionality.ipynb`](./concept_compositionality.ipynb)**: Includes code to calculate the log-probability shift of each pair of concepts.
 - **[`playroom.ipynb`](./playroom.ipynb)**: While not strictly a part of any experiment, this notebook contains code to generate samples from a model steered towards one or more concepts.

## Data
Inside the **[`data_hub`](./data_hub)** directory, you can find the following files: 
 - **[`concepts.csv`](./data_hub/concepts.csv)**: Contains the dataset of concepts used for our overall concept steerability experiments. For each concept, it includes the positive and negative prompts for both Type 1 (concept-only) and Type 2 (counterbalanced) prompt formulations, as well as the positive and negative labels for the evaluation of steering success with all-MiniLM-L6-v2.
 - **[`evaluation_prompts.txt`](./data_hub/evaluation_prompts.txt)**: Contains a curated list of neutral, open-ended sentence evaluation prompts (e.g., *"I was just thinking about something earlier today..."*) we used in our concept steerability experiments.
 - **[`log_prob_shift_keywords.csv`](./data_hub/log_prob_shift_keywords.csv)**: Contains the target keywords used for our token log-probability shift experiment. It maps each concept/hypothesis to a set of related keywords.
  
## Results
The results of our experiments can be found in **[`results`](./results)**.
The results of the **Concept Steerability** experiment can be found under **[`concept_steerability_results`](./results/concept_steerability_results)**, and includes:
 - **[`optimal_layer_graphs`](./results/concept_steerability_results/optimal_layer_graphs)**: Consists of graphs detailing the performance of each concept at each layer of injection.
 - **[`optimal_parameters.csv`](./results/concept_steerability_results/optimal_parameters.csv)**: Includes the optimal layer of injection for each concept.
 - **[`bert_scores.csv`](./results/concept_steerability_results/bert_scores.csv)**: Includes the final score of each concept injected at its optimal layer.

The results of the **Concept Compositionality** experiment can be found under **[`concept_compositionality_results`](./results/concept_compositionality_results)**, and includes the log-probability shift of each pair of concepts.

## Result Analysis
Inside the **[`result_analysis`](./result_analysis)** directory there are many python scripts designed to analyze the results of our experiments:
 - **[`iterative_k_means_optimal_layer.py`](./result_analysis/iterative_k_means_optimal_layer.py)**: Finds semantic clusters with low optimal layer standard deviation.
 - **[`iterative_k_means_steering.py`](./result_analysis/iterative_k_means_steering.py)**: Finds semantic clusters with low steering standard deviation.
 - **[`optimal_layers.py`](./result_analysis/optimal_layers.py)**: Plots concepts by optimal layer.
 - **[`pca_semantic_visualization.py`](./result_analysis/pca_semantic_visualization.py)**: Creates interactive 3d plot of concept semantics and steerability.
 - **[`prompt_formulation_impact.py`](./result_analysis/prompt_formulation_impact.py)**: Plots graph of Type 1 (concept-only) prompts vs Type 2 (counterbalanced) prompts and calculate correlation parameters.
 - **[`steerability_scores.ipynb`](./result_analysis/steerability_scores.ipynb)**: Notebook to plot a graph combining each concept with its optimal layer and steering value.

## Acknowledgments
The **[`activation_additions`](./activation_additions)** module used in this repository is a modified, stripped-down version of the **[original codebase](https://zenodo.org/records/13879423)** provided by **[Turner et al. (2023)](https://arxiv.org/abs/2308.10248)** in their foundational paper on Activation Addition. We thank the authors for open-sourcing their implementation.
