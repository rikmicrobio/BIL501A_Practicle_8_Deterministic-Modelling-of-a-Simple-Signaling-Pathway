# Practical 8: Deterministic Modelling of a Simple Signaling Pathway Using ODEs

A beginner-friendly computational biology practical introducing students to **deterministic modelling of biological systems using Ordinary Differential Equations (ODEs)** with Python.

## Overview

This lesson connects a simple biological signaling pathway with computational modelling:

```text
External or Internal Signal
            |
            v
     Inactive Protein
            |
       activation
            |
            v
     Activated Protein
            |
        activates
            |
            v
      Cellular Response
```

The practical asks a simple biological question:

> **If a signal is present, how does the amount of an activated protein and a downstream cellular response change with time?**

Students first understand the biological process and the idea of a mathematical model, and only then implement and simulate the model in Python.

## Learning Level

**Beginner**

This practical is specifically designed for Master's students who may have:

- little or no Python programming experience
- limited mathematical background
- no prior experience with differential equations

Students are **not expected to solve the ODEs manually**. The emphasis is on understanding the biological meaning of the model, running the computational simulation, visualizing the results, and interpreting the biology.

## Learning Objectives

By the end of this practical, students should be able to:

1. Describe a simple cellular signaling pathway.
2. Explain the meaning of a deterministic model.
3. Understand an ODE as a rule describing how a biological quantity changes with time.
4. Identify model parameters and initial conditions.
5. Implement a simple ODE model in Python.
6. Use SciPy to numerically solve an ODE system.
7. Plot biological quantities as a function of time.
8. Investigate how changing model parameters affects signaling.
9. Interpret simulation results in biological terms.

## Biological Model

The model contains two dynamic variables:

- **A** — activated protein
- **R** — downstream cellular response

The signal **S** is treated as a constant input.

The biological processes are simplified as:

```text
Signal
  |
  | activates
  v
Activated Protein
  |
  | produces
  v
Cellular Response
```

At the same time, both components can be removed:

```text
Activated Protein  -----> removal/deactivation
Cellular Response  -----> degradation/removal
```

## Mathematical Model

The model is expressed using two ODEs.

### Activated protein

The change in activated protein is:

**activation − removal**

$$
\frac{dA}{dt} = k_1S - k_2A
$$

### Cellular response

The change in cellular response is:

**production − removal**

$$
\frac{dR}{dt} = k_3A - k_4R
$$

Students are introduced to these equations only after understanding their biological meaning.

## Model Parameters

| Symbol | Meaning | Biological interpretation |
|---|---|---|
| `S` | Signal concentration | Strength of the incoming signal |
| `k1` | Protein activation rate | How strongly the signal activates the protein |
| `k2` | Protein deactivation/removal rate | How quickly activated protein is removed |
| `k3` | Response production rate | How strongly activated protein produces the response |
| `k4` | Response removal rate | How quickly the response is removed |

## Initial Conditions

The simulation begins with:

```text
Activated protein = 0
Cellular response = 0
```

This represents a simplified inactive starting state.

## Computational Workflow

The practical follows this workflow:

```text
Biological System
       |
       v
Define Biological Processes
       |
       v
Translate Processes into Simple Mathematical Rules
       |
       v
Define ODE Model
       |
       v
Implement in Python
       |
       v
Solve Numerically with SciPy
       |
       v
Visualize with Matplotlib
       |
       v
Interpret Biological Behaviour
```

## Python Libraries

The practical uses:

- **NumPy** — numerical arrays and time points
- **SciPy** — numerical solution of the ODE system
- **Matplotlib** — visualization
- **Jupyter Notebook** — interactive learning environment

## Installation

### Option 1: Using pip

Run the following command in a terminal:

```bash
pip install numpy scipy matplotlib jupyter
```

If your system uses `pip3`:

```bash
pip3 install numpy scipy matplotlib jupyter
```

### Option 2: Google Colab

No separate installation is normally required for NumPy, SciPy, and Matplotlib in Google Colab.

## Running the Practical

Open:

```text
Practical_8_Signaling_Pathway_ODEs.ipynb
```

Then execute the notebook **cell by cell from the beginning**.

The notebook is deliberately structured so that students first encounter:

1. Biology
2. Conceptual explanation
3. Simple mathematics
4. Python implementation
5. Numerical simulation
6. Visualization
7. Biological interpretation

## Key Python Function

The ODE system is solved using SciPy's:

```python
solve_ivp()
```

Students do not need to understand the numerical algorithm in detail. At this stage, they should understand that `solve_ivp()` takes the model rules and calculates how the system changes over time.

## Experiments

Students investigate how the signaling system responds when parameters are changed.

### Experiment 1 — Signal strength

Compare:

```text
S = 0.5
S = 1.0
S = 2.0
```

**Question:**

> How does increasing signal strength affect the downstream cellular response?

### Experiment 2 — Protein deactivation

Compare different values of `k2`.

**Question:**

> What happens when activated protein is removed more rapidly?

### Experiment 3 — Response production

Change `k3`.

**Question:**

> How does changing the rate of response production affect the cellular response?

### Experiment 4 — Response removal

Change `k4`.

**Question:**

> What happens when the cellular response is removed more rapidly?

## What Students Should Observe

The simulation illustrates several important concepts:

- A biological signal can change molecular concentrations over time.
- Activated protein appears before the downstream response.
- Production and removal processes can produce a steady state.
- Changing a model parameter can change the magnitude and dynamics of the response.
- Mathematical models can be used to explore biological hypotheses computationally.

## Steady State

A steady state occurs when production and removal become approximately balanced.

For example:

```text
Production ≈ Removal
        |
        v
Net change ≈ 0
        |
        v
Concentration becomes approximately stable
```

For the activated protein:

$$
A_{ss} = \frac{k_1S}{k_2}
$$

For the cellular response:

$$
R_{ss} = \frac{k_3A_{ss}}{k_4}
$$

Students are not required to derive these equations manually.

## Student Exercises

Students are asked to:

- change the signal concentration
- change activation and removal rates
- rerun the simulation
- compare plots
- identify changes in the steady-state response
- explain their observations in biological language

## Troubleshooting

### `ModuleNotFoundError`

Example:

```text
ModuleNotFoundError: No module named 'scipy'
```

Install the missing library:

```bash
pip install scipy
```

### `NameError`

If Python reports that a variable is not defined, run the notebook cells from the beginning in order.

In Jupyter, you can use:

```text
Kernel → Restart Kernel and Run All Cells
```

### Image or file not found

If the notebook uses an external image, make sure the image is located in the correct repository directory. The recommended repository structure is:

```text
BIC502A_Unit_08_ODE_Signaling_Model/
│
├── Practical_8_Signaling_Pathway_ODEs.ipynb
├── README.md
└── images/
    └── signaling_pathway.png
```

## Assessment Questions

At the end of the practical, students should be able to answer:

1. What is a deterministic model?
2. What does an ODE represent in this biological model?
3. What does `S` represent?
4. What does `k1` represent?
5. What happens when the signal strength increases?
6. What happens when protein deactivation becomes faster?
7. What is a steady state?
8. What does `solve_ivp()` do?
9. Why do we need initial conditions?
10. How can computational modelling help us understand biological signaling?

## Key Take-Home Message

The practical introduces a general computational biology workflow:

```text
Biological Question
        ↓
Biological Mechanism
        ↓
Mathematical Model
        ↓
Python Implementation
        ↓
Numerical Simulation
        ↓
Visualization
        ↓
Biological Interpretation
```

The goal is **not** to teach advanced mathematics. The goal is to help students understand how a biological process can be represented as a computational model and explored using Python.

## Repository

Suggested repository name:

```text
BIC502A_Unit_08_ODE_Signaling_Model
```

Suggested notebook:

```text
Practical_8_Signaling_Pathway_ODEs.ipynb
```

---

**Course:** Bioinformatics / Computational Biology  
**Practical:** 8  
**Topic:** Deterministic Modelling of a Simple Signaling Pathway Using ODEs  
**Level:** Master's / Beginner
