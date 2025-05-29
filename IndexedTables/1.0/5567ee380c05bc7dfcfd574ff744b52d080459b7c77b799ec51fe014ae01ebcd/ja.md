```
reindex(t::IndexedTable, by)
reindex(t::IndexedTable, by, select)
```

テーブル `t` を新しい主キー `by` で再インデックスし、オプションで `select` を介して列のサブセットを保持します。 [`NDSparse`](@ref) の場合は、[`selectkeys`](@ref) を使用してください。

# 例

```
t = table([2,1],[1,3],[4,5], names=[:x,:y,:z], pkey=(1,2))

t2 = reindex(t, (:y, :z))

pkeynames(t2)
```
