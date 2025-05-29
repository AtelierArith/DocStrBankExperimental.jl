```
incompatibility_robustness(
    A::Vector{Measurement{<:Number}};
    noise::String = "general",
    return_parent::Bool = false,
    verbose::Bool = false,
    solver = Hypatia.Optimizer{_solver_type(T)})
```

Computes the incompatibility robustness of the measurements in the vector `A`. Depending on the noise model chosen, the second argument can be "depolarizing" (`{tr(Aₐ)I/d}ₐ`, where `d` is the dimension of the system), "random" (`{I/n}ₐ`, where `n` is the number of outcomes), "probabilistic" (`{pₐI}ₐ`, where `p` is a probability distribution), "jointly_measurable", or "general" (default). Returns the parent POVM if `return_parent = true`.

References:

  * Designolle, Farkas, Kaniewski, [arXiv:1906.00448](https://arxiv.org/abs/1906.00448) (for the different noise models)
  * Gühne et al., [arXiv:2112.06784](https://arxiv.org/abs/2112.06784) (Section III.B.2)
