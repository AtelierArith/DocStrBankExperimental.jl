```
reset!(brkga_data::BrkgaData)
```

すべての集団を新しいキーでリセットします。 [`set_initial_population!`](@ref) によって提供されたすべてのウォームスタートソリューションは破棄されます。再度それらのソリューションを挿入するには、[`inject_chromosome!`](@ref) を使用できます。

!!! warning
    [`evolve!()`](@ref) と同様に、デコーディングはスレッドを使用して並行して行われ、ユーザーは **デコーダがスレッドセーフであることを保証しなければなりません。** そのような特性が保持できない場合は、環境変数 `JULIA_NUM_THREADS = 1` を設定して単一スレッドを使用することをお勧めします [(Juliaの並列計算を参照)](https://docs.julialang.org/en/v1.1/manual/parallel-computing/)


# 例外をスロー

  * `ErrorException`: [`initialize!`](@ref) が事前に呼び出されていない場合。
