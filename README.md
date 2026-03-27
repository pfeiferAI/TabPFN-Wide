# TabPFN-Wide

> **Deprecated:** This repository is deprecated. Please use the new repository: https://github.com/not-a-feature/TabPFN-Wide

This repository provides code and utilities for training and evaluating wide TabPFN-Wide models on multi-omics and tabular datasets. It includes scripts, reusable modules, analysis tools, and pretrained models.

## Repository Structure

- `tabpfnwide/`  
   Core package with training scripts, data loaders, utility functions, and patches.
   - `train.py`, `data.py`, `utils.py`, etc.: Main codebase.
   - `patches.py`: Contains patches for TabPFN.
- `analysis/`  
   Scripts for analyzing results and comparing model performance.
    - `multiomics_feature_reduction.py`: Benchmarking on multi-omics datasets.
    - `openml_benchmark.py`: Benchmarking on OpenML datasets.
    - `openml_widening.py`: Code for feature-smearing and needle-in-a-haystack experiments.
    - `extract_widened_attention.py`: Script for extracting attention of feature-smearing and needle-in-a-haystack datasets.
    - `extract_multi_omics_attention.py`: Script for extracting attention of a multi-omics dataset to apply biological interpretation.
- `models/`  
   Pretrained model checkpoints.
- `multiomics_benchmark_data/`, `shamir_data/`  
   Placeholder directories for datasets.
- `tabpfn_wide_example.ipynb`, `tabpfn_wide_attention.ipynb`  
   Example Jupyter notebooks. 
- `requirements.txt`  
   List of required Python packages.
- `setup.py`, `pyproject.toml`  
   Packaging and installation files.

## Patching and API Stability

This project uses patches (see `tabpfnwide/patches.py`) to extend or modify the behavior of external libraries such as TabPFN. This approach makes it easy to share and inject new functionality without modifying the original source code.

**However, please note:**
The APIs of the TabPFN package and related dependencies have changed and are actively changing. Patches may break unexpectedly with new releases, leading to subtle bugs or runtime errors. The current implementation is tested with the versions specified in `requirements.txt`. However, we note that the patches are not necessary for training and using TabPFN-Wide models, but only for the analysis scripts as well as extracting attention weights.

## Setup
1. Create and activate a Python environment (e.g., with conda or venv).
2. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```
3. Install the package:
    ```bash
    pip install -e .
    ```

## Usage

- To train a model, run the `train.sh`script with the desired parameters.
- See the example notebooks for usage demonstrations of the pre-trained models.

## Data

- Place the datasets in the appropriate folders (`multiomics_benchmark_data/`, `shamir_data/`).
- Data loading utilities are provided in `tabpfnwide/data.py` and `tabpfnwide/load_mm_data.py`.

## Pretrained Models

Pretrained model checkpoints are available in the `models/` directory.

## Comparison with TabPFNv2
For comparison with TabPFNv2, we used the original TabPFNv2 model available at `https://huggingface.co/Prior-Labs/TabPFN-v2-clf/blob/main/tabpfn-v2-classifier.ckpt`. From package version 2.1.0 the `tabpfn` package per default uses the Real-TabPFN model. To replicate our results, please download the original TabPFNv2 model and load it explicitly in the code using the `model_path` argument of the `TabPFNClassifier`.
