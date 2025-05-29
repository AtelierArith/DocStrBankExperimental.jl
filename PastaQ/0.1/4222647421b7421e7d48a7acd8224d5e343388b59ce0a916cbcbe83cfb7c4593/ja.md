```
fidelity(ψ::MPS, ρ::MPO; kwargs...)
fidelity(ρ::MPO, ψ::MPS; kwargs...)
```

MPS波動関数とMPO密度演算子間の量子状態の忠実度：

$$
F(\psi,\rho) = \langle\psi|\rho|\psi\rangle.
$$
