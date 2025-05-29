```
SteepestDescentCoefficient()
SteepestDescentCoefficient(M::AbstractManifold)
```

[`conjugate_gradient_descent`](@ref)アルゴリズムの更新係数を計算し、[`gradient_descent`](@ref)メソッドにフォールバックします。すなわち、

$$
β_k = 0
$$

!!! info
    この関数は[`SteepestDescentCoefficient`](@ref)のための[`ManifoldDefaultsFactory`](@ref)を生成します。多様体に依存するデフォルト値については、このファクトリは、例えば対応する[`AbstractManoptSolverState`](@ref)から多様体が利用可能になるまで構築を延期します。

