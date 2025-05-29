```
spectrum(H::QuantumObject,
    ωlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple},
    A::QuantumObject{Operator},
    B::QuantumObject{Operator};
    solver::SpectrumSolver=ExponentialSeries(),
    kwargs...)
```

Calculate the spectrum of the correlation function

$$
S(\omega) = \int_{-\infty}^\infty \lim_{t \rightarrow \infty} \left\langle \hat{A}(t + \tau) \hat{B}(t) \right\rangle e^{-i \omega \tau} d \tau
$$

See also the following list for `SpectrumSolver` docstrings:

  * [`ExponentialSeries`](@ref)
  * [`PseudoInverse`](@ref)
