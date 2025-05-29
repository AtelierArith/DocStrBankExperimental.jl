```
fidelity_susceptibility(state::Union{FiniteMPS,InfiniteMPS}, H₀::T,
                        Vs::AbstractVector{T}, [henvs=environments(state, H₀)];
                        maxiter=Defaults.maxiter,
                        tol=Defaults.tol) where {T<:MPOHamiltonian}
```

基底ハミルトニアン `H₀` の基底状態 `state` の忠実度感受性を、摂動ハミルトニアンのセット `Vs` に関して計算します。各摂動ハミルトニアンは、'全体' ハミルトニアン $H = H₀ + ∑ᵢ aᵢ Vᵢ$ における調整パラメータ $aᵢ$ に対応すると解釈できます。

摂動ハミルトニアンのそれぞれに対応する `state` 上の基本的な励起の重なりを含む行列を返します。
