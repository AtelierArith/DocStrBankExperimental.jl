```
num_to_name(tree::HybridNetwork)
```

与えられた木のための分類群番号とその名前を含むテーブルを取得します。

# 引数

  * `tree`: 木を含むHybridNetworkオブジェクト

# 出力

分類群番号とその名前を示す`Dict{Int64, Any}`

# 例

```jldoctest
julia> num_to_name(readTopology("(O:3.866,(HYB:1.593,(P1:1.208,P2:1.208):0.386):2.273);"))
Dict{Int64, Any} with 4 entries:
  4 => "P2"
  2 => "O"
  3 => "P1"
  1 => "HYB"
```
