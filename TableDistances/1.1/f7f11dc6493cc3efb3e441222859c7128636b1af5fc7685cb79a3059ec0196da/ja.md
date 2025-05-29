```
TableDistance(; normalize=true, weights=nothing)
```

Tables.jl テーブルの行間の距離。

## オプション

  * `normalize` - 距離を計算する前にテーブルの列を正規化するかどうか               （デフォルトは `true`）
  * `weights`   - 各列の重みを持つ辞書               （デフォルトは均一な重み）

## 例

```julia
julia> pairwise(TableDistance(), table₁, table₂)
```
