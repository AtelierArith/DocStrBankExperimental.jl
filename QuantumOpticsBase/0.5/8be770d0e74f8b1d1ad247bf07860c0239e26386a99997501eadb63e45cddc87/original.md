```
liouvillian(H, J; rates, Jdagger)
```

Create a super-operator equivalent to the master equation so that $\dot ρ = S ρ$.

The super-operator $S$ is defined by

$$
S ρ = -\frac{i}{ħ} [H, ρ] + \sum_i J_i ρ J_i^† - \frac{1}{2} J_i^† J_i ρ - \frac{1}{2} ρ J_i^† J_i
$$

# Arguments

  * `H`: Hamiltonian.
  * `J`: Vector containing the jump operators.
  * `rates`: Vector or matrix specifying the coefficients for the jump operators.
  * `Jdagger`: Vector containing the hermitian conjugates of the jump operators. If they            are not given they are calculated automatically.
