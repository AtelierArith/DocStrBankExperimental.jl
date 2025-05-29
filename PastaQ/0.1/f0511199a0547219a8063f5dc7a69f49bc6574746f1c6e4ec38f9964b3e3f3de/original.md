```
getsamples(
  M::Union{LPDO,MPO,ITensor},
  preps::Matrix,
  bases::Matrix,
  nshots::Int;
  kwargs...
)
```

Generate a set of process measurement data acccording to a set of input states `preps` and measurement `bases`, performing `nshots` measurements per configuration. For a single measurement, the input state $|\xi\rangle=\otimes_j|\xi_j\rangle$ is evolved according to the channel $M$, and then measured in a given measurement basis. The probability that the final state returns outcome $\sigma = (\sigma_1,\sigma_2,\dots)$ in the basis defined by $U$ is given by

$$
P(\sigma|\xi) = \text{Tr}\big[(\rho_\xi^T\otimes 1)\Lambda_{M} \big]
$$

where $\rho_\xi = |\xi\rangle\langle\xi|$ and $\Lambda_M$ is the Choi matrix.
