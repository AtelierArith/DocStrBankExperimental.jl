```
evolve!(brkga_data::BrkgaData, num_generations::Int64 = 1)
```

現在の集団を、`num_generations` 世代のためにマルチペアレント BRKGA のガイドラインに従って進化させます。

!!! warning
    デコーディングはスレッドを使用して並行して行われ、ユーザーは **デコーダがスレッドセーフであることを保証しなければなりません。** そのような特性が保持できない場合は、環境変数 `JULIA_NUM_THREADS = 1` を設定して単一スレッドを使用することをお勧めします [(Juliaの並列計算を参照)](https://docs.julialang.org/en/v1.1/manual/parallel-computing/)。


# 例外をスロー

  * `ErrorException`: [`initialize!()`](@ref) が呼び出されていない場合。
  * `ArgumentError`: `num_generations < 1` の場合。
