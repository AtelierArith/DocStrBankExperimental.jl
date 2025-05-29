```
kpm_density(
    N::Int, μ::T, W
) where {T<:AbstractVector}
```

KPMモーメント$\mu$を考慮して、$N$エネルギーポイント$\epsilon$で対応するスペクトル密度$\rho(\epsilon)$を評価します。ここで、$W$はスペクトルバンド幅またはスペクトルの範囲です。この関数は$\rho(\epsilon)$と$\epsilon$の両方を返します。
