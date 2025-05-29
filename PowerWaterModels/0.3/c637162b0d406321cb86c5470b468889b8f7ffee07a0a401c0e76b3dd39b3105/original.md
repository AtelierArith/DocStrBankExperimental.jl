Objective for minimizing the maximum difference between time-adjacent power generation variables. Note that this function introduces a number of auxiliary variables and constraints to appropriately model the objective. Mathematically, the objective and auxiliary terms are modeled as follows:

$$
    \begin{aligned}
    & \text{minimize} & & z \\
    & \text{subject to} & & z \geq pg_{i, c, t} - pg_{i, c, t-1}, \, \forall i \in \mathcal{G}, \, \forall c \in \mathcal{C}, \, \forall t \in \{2, 3, \dots, T\} \\
    & & & z \geq pg_{i, c, t-1} - pg_{i, c, t}, \, \forall i \in \mathcal{G}, \, \forall c \in \mathcal{C}, \, \forall t \in \{2, 3, \dots, T\} \\
    & & & z \geq 0 \\
    & & & x \in \mathcal{X},
    \end{aligned}
$$

where $\mathcal{G}$ is the set of generators, $\mathcal{C}$ is the set of conductors, and $\{2, 3, \dots, T\}$ are the non-starting time indices. Further, $x \in \mathcal{X}$ represents the remainder of the problem formulation, i.e., variables and constraints not relevant to this description.
