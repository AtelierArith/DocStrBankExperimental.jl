```
get_best_chromosome(brkga_data::BrkgaData)::Array{Float64, 1}
```

これまでにすべての集団の中で見つかった最良の個体のコピーを返します。

# 例外をスローします

  * `ErrorException`: [`initialize!`](@ref) が事前に呼び出されていない場合。
