```
fidelity(Ψ::MPS, ϱ::LPDO{MPO}; cutoff::Float64 = 1e-15)
fidelity(ϱ::LPDO{MPO}, ψ::MPS; kwargs...)
```

MPS波動関数とLPDO密度演算子間の量子状態の忠実度 $\varrho=XX^\dagger$

$$
F(\psi,\rho) = \langle\psi|\varrho|\psi\rangle = |X^\dagger|\psi\rangle|^2.
$$
