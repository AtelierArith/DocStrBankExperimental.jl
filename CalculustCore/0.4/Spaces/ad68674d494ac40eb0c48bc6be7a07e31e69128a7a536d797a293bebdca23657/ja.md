```julia
diffusionOp(ν, V, discr; ν_update_func)

```

拡散演算子: -∇⋅(ν∇⋅)

`ν`は`V`内の空間変化する拡散係数である拡散演算子を返します。`ν`は`SciMLOperators.DiagonalOperator`と同じシグネチャを持つ`ν_update_func`によって更新できます。

`ν`は空間`V`の関数であると仮定されています。ただし、`V`が変換された空間である場合、`ν`は物理空間の関数、すなわち`transform(V)`であるとします。
