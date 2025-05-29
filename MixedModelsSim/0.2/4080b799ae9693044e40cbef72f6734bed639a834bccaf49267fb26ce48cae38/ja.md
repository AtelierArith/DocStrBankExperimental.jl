```
nlevstbl(nm::Symbol, n, vars::Pair{Symbol, Vector{String}}...)
```

`nm` 列を `PooledArray` として `n` レベルを持つ `Tables.columntable` を返します。

もし `vars` ペアが与えられた場合、それらは `nm` 列の特性を表す列に展開されます。実験デザインの用語で言えば、例えば `nm` が `:item` であれば、これらはアイテム間の実験要因を表します。

`nm` 列は `nlevels(n, uppercase(first(string(nm))))` として生成されます。

# 例

```julia-repl
julia> nlevstbl(:item, 10)
(item = ["I01", "I02", "I03", "I04", "I05", "I06", "I07", "I08", "I09", "I10"],)

julia> nlevstbl(:item, 9, :level => ["low", "medium", "high"])
(item = ["I1", "I2", "I3", "I4", "I5", "I6", "I7", "I8", "I9"], level = ["low", "medium", "high", "low", "medium", "high", "low", "medium", "high"])
```
