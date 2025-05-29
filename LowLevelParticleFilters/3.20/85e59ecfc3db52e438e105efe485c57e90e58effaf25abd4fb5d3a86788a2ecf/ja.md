```
WikiParams(; α = 1.0, β = 0.0, κ = 1.0)
WikiParams(; ακ = 1.0, β = 0.0) # ακのためのパラメータが1つだけの簡略化されたインターフェース
```

Unscented transform parameters suggested at [Wiki: Kalman*filter#Sigma*points](https://en.wikipedia.org/wiki/Kalman_filter#Sigma_points).

  * `α`: シグマポイントの広がりのためのスケーリングパラメータ (0,1]。広がりを減らすには`α`を減少させる。
  * `β`: 状態の分布に関する事前知識を組み込む。
  * `κ`: 通常3nx/2または1に設定される二次スケーリングパラメータ。シグマポイントの広がりを増やすには`κ`を増加させる。

$$
α^2 κ < L
$$

の場合、ここで$L$はシグマポイントの次元であり、中心平均重みは負になります。これは許可されていますが、場合によっては不定の共分散行列につながる可能性があります。

ポイントの広がりは$α^2 κ$であり、ポイントの次元には依存しません。広がりを視覚化するには

```julia
using Plots
μ = [0.0, 0.0]
Σ = [1.0 0.0; 0.0 1.0]
pars = LowLevelParticleFilters.WikiParams(α = 1.0, β = 0.0, κ = 1.0)
xs = LowLevelParticleFilters.sigmapoints(μ, Σ, pars)
unscentedplot(xs, pars)
```

簡略化された調整ルール 

  * シグマポイントの広がりを減少させたい場合は、$κ = 1$および$α < 1$を使用します。
  * シグマポイントの広がりを増加させたい場合は、$κ > 1$および$α = 1$を使用します。

このルールは、単一の関数引数$ακ$のみを持つインターフェースを使用する際に使用できます。詳細については、Nielsen, K. et al., 2021, "UKF Parameter Tuning for Local Variation Smoothing"を参照してください。

[`MerweParams`](@ref)および[`TrivialParams`](@ref)も参照してください。
