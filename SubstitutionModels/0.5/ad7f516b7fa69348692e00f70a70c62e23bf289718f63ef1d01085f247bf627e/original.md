Generate a Q matrix for a `NucleicAcidSubstitutionModel`, of the form:

$$
Q = \begin{bmatrix}
Q_{A, A} & Q_{A, C} & Q_{A, G} & Q_{A, T} \\
Q_{C, A} & Q_{C, C} & Q_{C, G} & Q_{C, T} \\
Q_{G, A} & Q_{G, C} & Q_{G, G} & Q_{G, T} \\
Q_{T, A} & Q_{T, C} & Q_{T, G} & Q_{T, T} \end{bmatrix}
$$

Call as either

1. `Q(model)`, or
2. `Q(model, bool)`

Form (2) scales the matrix so that $_π(model) ⋅ -diag(Q(model)) = 1$ when bool=true. `Q(model, false)` is equivalent to `Q(model)`.
