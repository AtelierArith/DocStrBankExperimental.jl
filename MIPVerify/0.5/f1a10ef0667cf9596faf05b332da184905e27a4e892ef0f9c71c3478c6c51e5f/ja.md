```julia
struct ReLU <: MIPVerify.Layer
```

ReLU操作を表します。

`p(x)`は、`p`が`ReLU`のインスタンスであるとき、[`relu(x)`](@ref)の省略形です。
