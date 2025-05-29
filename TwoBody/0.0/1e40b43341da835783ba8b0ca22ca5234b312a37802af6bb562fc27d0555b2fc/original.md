`Hamiltonian(operator1, operator2, ...)`

$$
\hat{H} = \sum_i \hat{o}_i
$$

The Hamiltonian is the input for each solver. This is an example for the non-relativistic Hamiltonian of hydrogen atom in atomic units:

$$
\hat{H} = 
- \frac{1}{2} \nabla^2
- \frac{1}{r}
$$

```@example
H = Hamiltonian(
  NonRelativisticKinetic(ℏ =1 , m = 1),
  CoulombPotential(coefficient = -1),
)
```
