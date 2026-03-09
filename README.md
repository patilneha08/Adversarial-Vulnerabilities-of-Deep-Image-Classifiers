# Adversarial-Vulnerabilities-of-Deep-Image-Classifiers
# Adversarial Vulnerabilities of Deep Image Classifiers

This repository presents the implementation and results of adversarial attacks on pre-trained deep image classification models as part of **Deep Learning Project 3 (Spring 2025)**. The goal was to design constrained adversarial attacks that degrade the performance of ResNet-34 on the ImageNet-1K subset and evaluate their transferability to another model, DenseNet-121.

## Project Overview

Despite their impressive performance, deep neural networks are highly susceptible to small input perturbations. In this project, we demonstrate the brittleness of ResNet-34 by launching a series of adversarial attacks—Fast Gradient Sign Method (FGSM), Projected Gradient Descent (PGD), and a patch-based PGD—under strict L∞ and L0 constraints. We also analyze the transferability of these attacks to DenseNet-121.

**Key Results:**
- Clean Top-1 / Top-5 Accuracy (ResNet-34): 76.00% / 94.20%
- FGSM Accuracy: 3.00% / 19.00%
- PGD Accuracy: 1.50% / 9.90%
- Patch PGD Accuracy: 0.00% / 0.00%
- Transfer to DenseNet-121:
  - FGSM: 39.20% / 67.80%
  - PGD: 32.40% / 67.80%
  - Patch PGD: 69.80% / 89.60%

## Attack Tasks and Methodology

### Task 1: Clean Evaluation
- Evaluated ResNet-34 on 500 clean images across 100 ImageNet-1K classes.
- Used standard normalization and batch evaluation.
- Served as the performance benchmark.

### Task 2: FGSM Attack
- ε = 0.02
- One-step gradient update based on the cross-entropy loss.
- Maintained imperceptibility while inducing >70% performance drop.

### Task 3: PGD-Like Iterative Attack
- ε = 0.02, α = 0.001, 20 steps
- Iterative update with L∞ projection and clipping.
- Achieved >74.5% Top-1 accuracy degradation.

### Task 4: Patch-Based PGD Attack
- Perturbed only a 32x32 patch per image.
- ε = 0.5, α = 0.025, 20 steps
- Localized attack targeting a random patch using spatial masking.
- Reduced both Top-1 and Top-5 accuracy to 0.00%.

### Task 5: Transferability Evaluation
- Evaluated DenseNet-121 on all datasets.
- Demonstrated moderate transferability for global attacks (FGSM/PGD).
- Patch-based attack transferred poorly due to architectural specificity.

## Summary of Findings

- Iterative attacks (PGD) are more effective than single-step attacks (FGSM).
- Even localized perturbations can completely fool state-of-the-art models.
- Global pixel-based attacks transfer better across models than patch-based attacks.
- These findings expose critical gaps in adversarial robustness and underscore the importance of defenses in safety-critical applications.

## Repository Contents

- `project3_code.ipynb`: Jupyter notebook with implementation of all attack tasks, evaluation code, and result visualizations.
- Model loading and evaluation for ResNet-34 and DenseNet-121.
- Adversarial dataset generation, visualizations, and accuracy tracking.
- Links to visual examples (included in report and GitHub).

## Team Members

- Ruchi Jha 
- Neha Patil 
- Satvik Upadhyay 

## GitHub Repository

Complete code and visualizations are available at:  
[https://github.com/RuchiMJha/Adversarial-Vulnerabilities-of-Deep-Image-Classifiers/tree/main)

## License

This repository is intended for academic use only. All attack implementations were developed for educational purposes as part of NYU’s Deep Learning coursework.
