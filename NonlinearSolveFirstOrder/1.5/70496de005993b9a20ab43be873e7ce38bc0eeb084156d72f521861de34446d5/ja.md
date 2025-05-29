```
GeneralizedFirstOrderAlgorithm(;
    descent, linesearch = missing,
    trustregion = missing, autodiff = nothing, vjp_autodiff = nothing,
    jvp_autodiff = nothing, max_shrink_times::Int = typemax(Int),
    concrete_jac = Val(false), name::Symbol = :unknown
)
```

これは、第一階（ヤコビ行列を使用）非線形解法アルゴリズムの一般化です。最も一般的な例はニュートン-ラフソン法です。

ここでの第一階は微分の階数を指し、収束の階数と混同しないでください。

### キーワード引数

  * `trustregion`: トラスト領域法を使用したグローバリゼーション。これは[`NonlinearSolveBase.AbstractTrustRegionMethod`](@ref)インターフェースに従う必要があります。
  * `descent`: ステップを計算するために使用する降下法。この降下法は[`NonlinearSolveBase.AbstractDescentDirection`](@ref)インターフェースに従う必要があります。
  * `max_shrink_times`: アルゴリズムが終了する前にトラスト領域半径を縮小できる最大回数。
