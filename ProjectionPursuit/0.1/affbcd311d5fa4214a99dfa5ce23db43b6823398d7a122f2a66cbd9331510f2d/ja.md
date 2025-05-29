```
sphere_optimize
```

単位球面上で制約された与えられた目的関数を最適化します。

詳細については http://hdl.handle.net/10012/16710 を参照してください。

# 引数

  * `data::Matrix{Float64}`: 各行は観測値を含みます。
  * `object_fun::Function`: 単位球面上で定義された任意の目的関数。
  * `n_of_candidate::Int64=5`: 微細探索ステップにおける候補方向の数。
  * `unit_sphere=nothing`: 単位球面は事前に生成できます。デフォルトでは単位球面が自動的に生成されます。
  * `proj=nothing`: 以前に見つかった投影方向。 [`projection_pursuit`](@ref projection_pursuit) を参照してください。
  * `fnscale::Int64=-1`: 目的関数を最大化または最小化します。デフォルトは -1 で、これは目的関数を最大化することを意味します。目的関数を最小化する必要がある場合は、`fnscale=1` に設定します。
  * `par::Bool=true`: プログラムを並列で実行します。
  * `fast::Bool=true`: 高速アルゴリズムを使用して単位球面を生成します。 [`gensphere`](@ref gensphere) および [`fastgensphere`](@ref fastgensphere) を参照してください。
