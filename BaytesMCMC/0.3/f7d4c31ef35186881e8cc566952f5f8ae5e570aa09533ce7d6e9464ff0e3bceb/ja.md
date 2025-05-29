```julia
struct InvalidTree
```

開始ノードに対する相対位置を使用して、無効な（サブ）ツリーに関する情報。

1. `left < right` の場合、このツリーは *回転* していました。
2. `left == right` の場合、これは *分岐* ノードです。
3. `left == 1 && right == 0` は、無効なツリーに遭遇することなく最大深度に達するためのセンチネル値として使用されます（[`REACHED_MAX_DEPTH`](@ref)を参照）。他の `left > right` の値は許可されていません。

# フィールド

  * `left::Int64`
  * `right::Int64`
