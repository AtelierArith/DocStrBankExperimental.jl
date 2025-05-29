```
get_chromosome(brkga_data::BrkgaData, population_index::Int64,
               position::Int64)::Array{Float64, 1}
```

`population_index`の集団で`position`にランク付けされた染色体のコピーを返します。染色体はフィットネスによってランク付けされており、最良の染色体は位置1にあります。

# 例外をスローします

  * `ErrorException`: [`initialize!`](@ref)が呼び出されていない場合。
  * `ArgumentError`: `population_index < 1`または`population_index > num_independent_populations`の場合。
  * `ArgumentError`: `position < 1`または`position > population_size`の場合。
