```
DifferentiableExpectation{t}
```

微分可能なパラメトリック期待値 `E : θ -> 𝔼[f(X)]` のための抽象スーパタイプであり、ここで `X ∼ p(θ)` であり、その値と導関数はモンテカルロ平均で近似されます。

# サブタイプ

  * [`Reinforce`](@ref)
  * [`Reparametrization`](@ref)

# 呼び出しの振る舞い

```
(E::DifferentiableExpectation)(θ...; kwargs...)
```

モンテカルロ平均 `(1/S) ∑f(xᵢ)` を返します。ここで `xᵢ ∼ p(θ)` は独立同分布のサンプルです。

# 型パラメータ

  * `threaded::Bool`: サンプリングを並行して行うかどうかを指定します。

# 必要なフィールド

  * `f`: 期待値内で適用される関数。
  * `dist_constructor`: 確率分布のコンストラクタ。
  * `rng::AbstractRNG`: 擬似乱数生成器。
  * `nb_samples::Integer`: モンテカルロサンプルの数。
  * `seed::Union{Nothing,Integer}`: 擬似乱数生成器のシードで、各呼び出しの前にリセットされます。シードなしの場合は `nothing` に設定します。

フィールド `dist_constructor` は呼び出し可能であり、`dist_constructor(θ...)` が `p(θ)` に対応するオブジェクト `dist` を生成する必要があります。生成されたオブジェクト `dist` は以下を満たす必要があります：

  * `rand(rng, dist)` でサンプリングするための [Random API](https://docs.julialang.org/en/v1/stdlib/Random/#Hooking-into-the-Random-API)
  * `logdensityof(dist, x)` で対数尤度を計算するための [DensityInterface.jl API](https://github.com/JuliaMath/DensityInterface.jl)
