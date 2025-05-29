```
propagator(ψ₀::AbstractFiniteMPS, z::Number, H::MPOHamiltonian, alg::DynamicalDMRG; init=copy(ψ₀))
```

動的DMRGアルゴリズムを使用して、伝播子 $\frac{1}{E₀ + z - H}|ψ₀⟩$ を計算します。
