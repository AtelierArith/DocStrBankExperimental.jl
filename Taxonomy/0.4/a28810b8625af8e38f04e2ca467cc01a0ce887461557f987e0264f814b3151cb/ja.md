```
print_lineage(lineage::Lineage; kwargs...)
print_lineage(io::IO, lineage::Lineage; kwargs...)
```

指定された `IO` オブジェクトに系統のフォーマットされた表現を印刷します。

# 引数

  * `delim::AbstractString = ";"` - 種フィールド間の区切り文字。
  * `fill::Bool = false` - `true` の場合、`UnclassifiedTaxon` を印刷します。スキップが false の場合のみ利用可能です。
  * `skip::Bool = false` - `true` の場合、`UnclassifiedTaxon` と区切り文字の印刷をスキップします。
