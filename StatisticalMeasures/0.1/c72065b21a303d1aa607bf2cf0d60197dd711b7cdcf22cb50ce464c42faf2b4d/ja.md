```
measures(; trait_options...)
```

*実験的*であり、パッチリリース間での動作が壊れる可能性があります。

辞書 `dict` を返します。これは、StatisticalMeasures.jl によって提供される測定コンストラクタをキーとしています。`dict[constructor]` の値は、`constructor(args...)` 構文を使用して構築されたすべての測定で共有される特性（測定の「メタデータ」）に関する情報を提供します。

# 特性オプション

測定特性の値に基づいてフィルタリングすることができます。以下の例を参照してください。

```
using StatisticalMeasures
import ScientificTypesBase.Multiclass

julia> measures(
    observation_scitype = Union{Missing,Multiclass},
    supports_class_weights = true,
)
```

---

```
measures(y; trait_filters...)
measures(yhat, y; trait_filters...)
```

*実験的*であり、パッチリリース間での動作が壊れる可能性があります。

ScientificTypes.jl がインポートされていると仮定して、指定されたデータ引数 `(y,)` または `(yhat, y)` に適用できる測定を見つけます。引数には複数の観測値が含まれていると仮定されており（`MLUtils.getobs` を実装する型を持つ）、それに基づいています。

そのような測定のコンストラクタをキーとした辞書を返します。追加の `trait_filters` は、ゼロ引数の `measures` メソッドと同じです。

```julia
using StatisticalArrays
using ScientificTypes

julia> measures(rand(3), rand(3), supports_weights=false)
LittleDict{Any, Any, Vector{Any}, Vector{Any}} with 1 entry:
  RSquared => (aliases = ("rsq", "rsquared"), consumes_multiple_observations = true, can_re…
```

*警告.* マッチングは、提供された引数の *最初の* 観測値のみに基づいており、例えば `y` または `yhat` が `Union` や他の抽象要素型のベクトルである場合は注意して解釈する必要があります。
