```
BoundaryConditionDirichlet(boundary_value_function)
```

関数 `boundary_value_function` を使用して境界での値を指定するディリクレ境界条件を作成します。これは、方程式の正確な解を渡すことによって正確な境界値を指定する境界条件を作成するために使用できます。渡された境界値関数は、初期条件関数が呼び出されるのと同じ引数で呼び出されます。すなわち、

```julia
boundary_value_function(x, t, equations)
```

ここで `x` は座標を指定し、`t` は現在の時間、`equation` は対応する方程式系です。

# 例

```julia
julia> BoundaryConditionDirichlet(initial_condition_convergence_test)
```
