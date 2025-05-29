```
gibbs_loss([f], reg_or_samples, α::Real)
```

The Gibbs loss for maximum independent set defined as

$$
L = -1/α \log(\langle ψ|\exp(α \sum(n))|ψ\rangle),
$$

where `n` is the vertex set size.

# Arguments

  * `f`: optional, postprocessing callback function `f(config) -> config`.   The input `config` is an integer of type `Int`, the output   `config` can be a type supports [`count_vertices`](@ref)   e.g, an `AbstractVector` or an `Integer`.
  * `reg_or_samples` can be a register (`Yao.ArrayReg` or [`SubspaceArrayReg`](@ref))   or a list of measurement result (config) in `AbstractVector`.
  * `α::Real`: the parameter of Gibbs loss.
