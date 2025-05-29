```
abstract type TransientIMEXFEOperator <: TransientFEOperator end
```

`TransientFEOperator`を定義する残差の暗黙-明示分解：

```
residual(t, u, v) = implicit_residual(t, u, v)
                  + explicit_residual(t, u, v),
```

ここで

  * 暗黙の残差によって定義される暗黙の演算子は硬いと見なされ、暗黙的に解決されることを意図しています。
  * 明示の残差によって定義される明示の演算子は非硬いと見なされ、明示的に解決されることを意図しています。
  * 暗黙の残差と明示の残差の両方は`v`に対して線形です。

# 重要

明示の演算子は暗黙の演算子よりも1次元少なくなければならず、グローバル演算子の質量項が完全に暗黙の演算子に含まれるようにします。

# 必須

  * [`get_imex_operators(tfeop)`](@ref)

# 任意

  * [`get_test(tfeop)`](@ref)
  * [`get_trial(tfeop)`](@ref)
  * [`get_algebraic_operator(tfeop)`](@ref)
