```
wrapdims(df, UniqueVector, :val, :x, :y)
```

Converts at Tables.jl table to a `KeyedArray` + `NamedDimsArray` pair, using column `:val` for values, and columns `:x, :y` for names & keys. Optional 2nd argument applies this type to all the key-vectors.
