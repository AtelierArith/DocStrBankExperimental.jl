```
spectrum(H::QuantumObject,
    ωlist::AbstractVector,
    c_ops::Union{Nothing,AbstractVector,Tuple},
    A::QuantumObject{Operator},
    B::QuantumObject{Operator};
    solver::SpectrumSolver=ExponentialSeries(),
    kwargs...)
```

相関関数のスペクトルを計算します

$$
S(\omega) = \int_{-\infty}^\infty \lim_{t \rightarrow \infty} \left\langle \hat{A}(t + \tau) \hat{B}(t) \right\rangle e^{-i \omega \tau} d \tau
$$

次のリストも参照してください `SpectrumSolver` のドキュメント:

  * [`ExponentialSeries`](@ref)
  * [`PseudoInverse`](@ref)
