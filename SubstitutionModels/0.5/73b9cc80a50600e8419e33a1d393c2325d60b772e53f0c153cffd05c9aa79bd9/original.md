Generate a P matrix for a `NucleicAcidSubstitutionModel`, of the form:

$$
P = \begin{bmatrix}
P_{A, A} & P_{A, C} & P_{A, G} & P_{A, T} \\
P_{C, A} & P_{C, C} & P_{C, G} & P_{C, T} \\
P_{G, A} & P_{G, C} & P_{G, G} & P_{G, T} \\
P_{T, A} & P_{T, C} & P_{T, G} & P_{T, T} \end{bmatrix}
$$

for specified time

Call as either

1. `P(model, t)`, or
2. `P(model, t, bool)`

Form (2) obtains its probabilities from the scaled Q matrix if bool=true. Branch lengths estimated from a scaled P matrix are in units of expected number of substitutions per site. `P(model, t, false)` is equivalent to `P(model, t)`.
