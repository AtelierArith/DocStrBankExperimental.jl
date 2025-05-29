```
optimize(obj, p0::Vector{Float64}; lower_bounds=nothing, upper_bounds=nothing, vary=nothing)
```

初期パラメータ p0 を使用して、IterativeNelderMeadOptimizer ソルバーで目的関数 obj を最小化します。境界は追加の `Vectors` として提供することもできます。`vary` キーワードは、特定のパラメータを固定する必要がある場合にオプションの `BitVector` を受け入れます。戻り値は、次のプロパティを持つ NamedTuple です：

  * `pbest::Vector{Float64}`: 最適化された目的値 fbest に対応する最終パラメータ。
  * `fbest::Float64`: 最終的に最適化された目的値。
  * `fcalls::Int`: 総目的呼び出しの数。
  * `simplex::Matrix{Float64}`: 最終的な単体。
  * `iteration::Int`: 実行された反復の数。
