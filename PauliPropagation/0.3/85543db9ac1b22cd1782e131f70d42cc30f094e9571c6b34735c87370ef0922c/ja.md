```
transposecliffordmap(map_array::Vector{Tuple{UInt8,Int}})
```

クリフォードゲート `maparray` を転置して、出力マップが入力マップの逆になるようにします。例えば、`transposecliffordmap(clifford_map[:H])` は、ハダマードゲートの逆のマップを返しますが、それは同じマップです。
