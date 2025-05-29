```
namedtuple(lineage::Lineage; kwargs...)
```

`lineage`の`CanonicalRanks`のフィールド名を持つNamedTupleを返します。この関数は、`Lineage`を`DataFrame`に変換するのに便利です。

# 引数

  * `fill_by_missing::Bool = false` - `true`の場合、`UnclassifiedTaxon`の代わりに欠損を埋めます。
