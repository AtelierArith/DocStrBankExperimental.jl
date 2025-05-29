```
propose_delta(magnitude)
```

Generate a proposal function that adds a Gaussian perturbation to the existing spin state. In `:dipole` mode, the procedure is to first introduce a random three-vector perturbation $𝐒' = 𝐒 + |𝐒| ξ$ and then return the properly normalized spin $|𝐒| (𝐒'/|𝐒'|)$. Each component of the random vector $ξ$ is Gaussian distributed with a standard deviation of `magnitude`; the latter is dimensionless and typically smaller than one. 

In `:SUN` mode, the procedure is analogous, but now involving Gaussian perturbations to each of the $N$ complex components of an SU(*N*) coherent state.

In the limit of very large `magnitude`, this function coincides with [`propose_uniform`](@ref).

Consider also [`Langevin`](@ref) sampling, which is rejection free.
