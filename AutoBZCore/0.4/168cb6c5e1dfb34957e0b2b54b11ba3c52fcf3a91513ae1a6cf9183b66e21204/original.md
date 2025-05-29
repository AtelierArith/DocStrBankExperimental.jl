```
DOSProblem(H, domain, [p=NullParameters()])
```

Define a problem for the density of states of a Hermitian or self-adjoint operator depending on a parameter, H(p), on a given `domain` in its spectrum. The mathematical definition we use is

$$
D(E) = \sum_{k \in p} \sum_{\lambda \in \text{spectrum}(H(k))} \delta(E - \lambda)
$$

where $E \in \text{domain}$ and $\delta$ is the Dirac Delta distribution.

## Arguments

  * `H`: a linear operator depending on a parameter, H(p), that is finite dimensional (e.g: tight binding model) or infinite dimensional (e.g. DFT data)
  * `domain`: a set in the spectrum for which an approximation of the density-of-states is desired. Can be a single point, in which case the solution will return the estimated density of states at that eigenvalue, or an interval, in which case the solution will return a function approximation to the density of states on that interval in the spectrum that should be understood as a distribution or measure.
  * `p`: optional parameters on which `H` depends for which the density of states should sum over. Can be discrete (e.g. for `H` a Hamiltonian with spin degrees of freedom) or continuous (e.g. for `H` a Hamiltonian parameterized by crystal momentum).
