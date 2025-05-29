```
ccn([T::Type], s) -> CCN
```

入力`s`からCCNを構築します。

# 引数

  * `T::Type`（オプション） - CCNの型。型が指定されていない場合、入力`s`の形式に基づいて[`infer_ccn_type`](@ref)を使用して型の最良の推測が行われます。
  * `s::Union{AbstractString,Integer}` - CCNを作成するために解析する入力。

# 戻り値

指定された場合は具体的な型`T`のCCNを返し、そうでない場合は`s`の形式から型が推測されます。
