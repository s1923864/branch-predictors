# Branch Predictors: An Introduction

This repository contains implementations of various types of branch predictors commonly used in pipeline processors to optimize instruction flow. The predictors covered are Local, Gshare, and Tournament predictors. s1923864.pdf file how prediction accuracy changes with increasing PHT gates for each branch predictor on 3 benchmarks, which are gromacs, gobmk, and sjeng respectively. 

## Table of Contents

1. [Local Predictor](#local-predictor)
2. [Gshare Predictor](#gshare-predictor)
3. [Tournament Predictor](#tournament-predictor)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Contributing](#contributing)

## Local Predictor

The Local predictor utilizes a Local History Table (LHT) and a Pattern History Table (PHT). The LHT keeps track of the recent history of individual branches, and the PHT uses this information to make predictions.

### Features
- High accuracy for branches that have a stable but unique pattern.
- Utilizes local information for prediction, making it resilient against global noise.

### Limitations
- Consumes more memory compared to simpler predictors.
- Might be ineffective for branches with complex or irregular patterns.

## Gshare Predictor

The Gshare predictor is an improvement over the Global predictor. It combines global history with the branch's Program Counter (PC) to index into the Pattern History Table (PHT).

### Features
- Better differentiation between different branches that have similar global history.
- Reduced aliasing, leading to more accurate predictions.

### Limitations
- Somewhat more complex to implement than simpler predictors.
- Requires careful tuning of the XOR operation between global history and the PC.

## Tournament Predictor

The Tournament predictor combines both local and global predictors and uses a selector to choose between them.

### Features
- Combines the benefits of both local and global prediction.
- Uses a tournament selector to dynamically choose the more accurate predictor.

### Limitations
- Complex to implement and tune.
- Consumes more memory and computational resources.

## Installation

Clone this repository and compile the code as per the instructions.

```bash
git clone https://github.com/s1923864/branch-predictors.git
cd branch-predictors
