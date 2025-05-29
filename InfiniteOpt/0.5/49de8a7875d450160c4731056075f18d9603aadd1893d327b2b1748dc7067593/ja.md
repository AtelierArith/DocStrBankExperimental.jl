```
evaluate_derivative(dref::GeneralVariableRef, 
                    method::AbstractDerivativeMethod,
                    write_model::JuMP.AbstractModel)::Vector{JuMP.AbstractJuMPScalar}
```

`method`に従って評価された導関数`dref`の式を構築します。式は`lhs - rhs`の形であり、`lhs`は特定の無限パラメータのいくつかのサポートで評価された導関数の関数であり、`rhs`は特定の無限パラメータのいくつかのサポートで評価された導関数引数の関数です。例えば、点`t = 1`での有限差分法の場合、`lhs`は`Δt * ∂/∂t[T(1)]`であり、`rhs`は前方差分モードの場合に`T(1+Δt) - T(1)`となります。これは、`evaluate`のためのヘルパー関数として意図されており、このメソッドによって生成された式を使用して、式を0に設定することによって導関数の値を近似する制約を生成します。ただし、この関数を拡張して導関数を近似するためのカスタムメソッドをエンコードすることもできます。これは、メソッドが生成的である場合に`add_derivative_supports`を呼び出す必要があり、ユーザーは`make_reduced_expr`を使用することが便利であると考えるでしょう。
