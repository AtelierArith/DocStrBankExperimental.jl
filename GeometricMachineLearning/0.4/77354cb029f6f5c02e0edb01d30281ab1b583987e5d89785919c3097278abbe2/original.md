```
GlobalSection(Y)
```

Construct a global section for `Y`.  

A global section $\lambda$ is a mapping from a homogeneous space $\mathcal{M}$ to the corresponding Lie group $G$ such that 

$$
\lambda(Y)E = Y,
$$

Also see [`apply_section`](@ref) and [`global_rep`](@ref).

# Implementation

For an implementation of `GlobalSection` for a custom array (especially manifolds), the function [`global_section`](@ref) has to be generalized.
