```
Lag <: AbstractDelay

Lag{K}(frames::Int)
```

`Lag`は、ルール内から特定の前のフレームを使用して[`Grid`](@ref)を利用することを可能にし、`get`を使用します。これは[`Delay`](@ref)に似ていますが、シミュレーションの`tspan`に関連する量ではなく、整数のフレーム数を使用する必要があります。下限は最初のフレームです。

# 型パラメータ

  * `K::Symbol`: `init`内のグリッドの名前と一致します。

# 引数

  * `frames::Int`: 遅延させるフレーム数、1以上。

# 例

```julia
SomeRule(;
    someparam=Lag(:grid_a, Month(3))
    otherparam=1.075
)
```

WARNING: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、githubの問題を報告してください。
