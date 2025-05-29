```
get(gd::GroupedDataFrame, key, default)
```

グループ化された列の値に基づいてグループを取得します。

`key` は `GroupKey`、`NamedTuple` またはグループ化列の値の `Tuple` である可能性があります（`groupby` の `cols` 引数と同じ順序で）。また、`AbstractDict` である場合もあり、その場合は引数の順序は重要ではありません。

# 例

```jldoctest
julia> df = DataFrame(a=repeat([:foo, :bar, :baz], outer=[2]),
                      b=repeat([2, 1], outer=[3]),
                      c=1:6);

julia> gd = groupby(df, :a)
GroupedDataFrame with 3 groups based on key: a
First Group (2 rows): a = :foo
 Row │ a       b      c
     │ Symbol  Int64  Int64
─────┼──────────────────────
   1 │ foo         2      1
   2 │ foo         1      4
⋮
Last Group (2 rows): a = :baz
 Row │ a       b      c
     │ Symbol  Int64  Int64
─────┼──────────────────────
   1 │ baz         2      3
   2 │ baz         1      6

julia> get(gd, (a=:bar,), nothing)
2×3 SubDataFrame
 Row │ a       b      c
     │ Symbol  Int64  Int64
─────┼──────────────────────
   1 │ bar         1      2
   2 │ bar         2      5

julia> get(gd, (:baz,), nothing)
2×3 SubDataFrame
 Row │ a       b      c
     │ Symbol  Int64  Int64
─────┼──────────────────────
   1 │ baz         2      3
   2 │ baz         1      6

julia> get(gd, (:qux,), nothing)
```
