```
weighted_minimum_set_cover(solver, weights::AbstractVector, subsets::Vector{Vector{Int}}, num_items::Int)
```

重み付き最小集合被覆問題を解決します。

### 引数

  * `solver`: 使用するソルバー。`LPSolver`または`IPSolver`のインスタンスであることができます。
  * `weights::AbstractVector`: サブセットの重み。
  * `subsets::Vector{Vector{Int}}`: サブセットのベクター。
  * `num_items::Int`: 被覆する要素の数。

### 戻り値

選択されたサブセットのインデックスのベクター。
