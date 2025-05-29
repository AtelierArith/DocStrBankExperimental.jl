```
exchange_elite!(brkga_data::BrkgaData, num_immigrants::Int64)
```

エリート解を集団間で交換します。集団が与えられた場合、`num_immigrants` の最良の解が隣接する集団にコピーされ、彼らの劣った解を置き換えます。集団が1つだけの場合、何も行われません。

# 例外をスローします

  * `ErrorException`: [`initialize!`](@ref) が事前に呼び出されていない場合。
  * `ArgumentError`: `num_immigrants < 1` の場合。
  * `ArgumentError`: `num_immigrants ≥ ⌈population_size/num_independent_populations⌉ - 1` の場合。
