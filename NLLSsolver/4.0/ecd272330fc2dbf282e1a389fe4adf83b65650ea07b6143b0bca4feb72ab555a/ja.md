```
NLLSsolver.computeresidual(mycost, vars...)
```

`vars`を考慮して`mycost`によって生成された残差を計算します。戻り値はベクトルでなければなりません。

# 例

次のRosenbrock問題の場合

```julia
struct Rosenbrock <: NLLSsolver.AbstractResidual
    a::Float64
    b::Float64
end
```

ユーザーは次の関数を定義する必要があります。

```julia
NLLSsolver.computeresidual(res::Rosenbrock, x, y) = SVector(res.a * (1 - x), res.b * (x ^ 2 - y))
```

!!! tip
    残差の長さがコンパイル時に既知である場合、静的ベクトルを返します。


!!! note
    必要なユーザー特化型API関数です。

