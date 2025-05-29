```
get_best_fitness!(brkga_data::BrkgaData)::Float64
```

すべての集団の中でこれまでに見つかった最良の個体のフィットネス/値を返します。

# 例外をスローします

  * `ErrorException`: [`initialize!`](@ref) が事前に呼び出されていない場合。
