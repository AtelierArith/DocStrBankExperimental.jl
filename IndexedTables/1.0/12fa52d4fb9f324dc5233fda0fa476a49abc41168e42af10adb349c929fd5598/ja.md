```
collect_columns(itr)
```

`Tuples` または `NamedTuples` を反復する場合は、反復可能なものを `Columns` オブジェクトとして収集し、それ以外の場合は通常の `Array` として収集します。

# 例

```
s = [(1,2), (3,4)]
collect_columns(s)

s2 = Iterators.filter(isodd, 1:8)
collect_columns(s2)
```
