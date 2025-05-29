```
SequentialMonteCarlo(;
    samples::Int=10_000,
    seed::Integer=rand(UInt64),
    verbose::Bool=false,
    threaded::Bool=true
)
```

PRAS分析のための逐次モンテカルロシミュレーションパラメータ

再現性のためにランダムシードを固定することをお勧めします。

# 引数

  * `samples::Int=10_000`: サンプル数
  * `seed::Integer=rand(UInt64)`: ランダムシード
  * `verbose::Bool=false`: 進行状況を表示
  * `threaded::Bool=true`: マルチスレッドを使用

# 戻り値

  * `SequentialMonteCarlo`: PRASシミュレーション仕様
