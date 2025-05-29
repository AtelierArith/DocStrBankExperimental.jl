```
ProjectionPursuit(; tol=1e-6, maxiter=100, deg=5, perc=0.9, n=100, rng=Random.default_rng())
```

プロジェクション・パシュート多変量変換は、任意の多変量分布を標準多変量ガウス分布に変換します。

この反復アルゴリズムは、プロジェクションインデックス `I(α)` として知られる非ガウス性のスコアを最大化するプロジェクションの方向 `α` を繰り返し見つけます。`α` に沿って投影されたサンプルは、非ガウス構造を除去するために [`Quantile`](@ref) 変換で変換されます。回転した直交基底 `Q = [α ...]` の他の座標はそのまま残されます。

`Q` の非特異性は、`norm(det(Q)) ≥ tol` を保証することで制御されます。変換されたサンプルが標準多変量ガウス分布からランダムに生成された `n` サンプルの `perc`% よりも「よりガウス的」である場合、または反復回数が最大 `maxiter` に達した場合に、反復プロセスは終了します。

# 例

```julia
ProjectionPursuit()
ProjectionPursuit(deg=10)
ProjectionPursuit(perc=0.85, n=50)
ProjectionPursuit(tol=1e-4, maxiter=250, deg=5, perc=0.95, n=100)

# rngを使用して
using Random
rng = MersenneTwister(2)
ProjectionPursuit(perc=0.85, n=50, rng=rng)
```

詳細については [https://doi.org/10.2307/2289161](https://doi.org/10.2307/2289161) を参照してください。
