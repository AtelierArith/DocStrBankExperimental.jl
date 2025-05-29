```
AverageObservableLogger(observable::Function, T::DataType, n_steps::Integer;
                        n_blocks::Integer=1024)
```

システムの観測を定期的に記録し、実行中の経験的平均を保持するロガーです。

[`GeneralObservableLogger`](@ref) が観測の完全な記録を保持するのに対し、[`AverageObservableLogger`](@ref) はそうではありません。さらに、`values(logger::AverageObservableLogger; std::Bool=true)` を呼び出すと、現在の実行中の平均と、[Flyvbjerg and Petersen 1989](https://doi.org/10.1063/1.457480) で説明されているブロック平均法に基づくこの平均の標準偏差の推定値の2つの値が返されます。

# 引数

  * `observable::Function`: 平均が記録される観測量で、`observable(s::System, neighbors; n_threads::Integer)` メソッドをサポートしている必要があります。
  * `T::DataType`: `observable` によって返される型。
  * `n_steps::Integer`: 観測間のシミュレーションステップ数。
  * `n_blocks::Integer=1024`: ブロック平均法で使用されるブロックの数で、偶数である必要があります。
