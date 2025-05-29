```
get(gd::GroupedDataFrame, key, default)
```

Get a group based on the values of the grouping columns.

`key` may be a `GroupKey`, `NamedTuple` or `Tuple` of grouping column values (in the same order as the `cols` argument to `groupby`). It may also be an `AbstractDict`, in which case the order of the arguments does not matter.

# Examples

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
