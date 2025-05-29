```
BoundaryConditionNeumann(boundary_normal_flux_function)
```

`BoundaryConditionDirichlet`と同様ですが、境界での法線フラックスの値を指定するために`boundary_normal_flux_function`を使用する放物線方程式のためのノイマン境界条件を作成します。渡された境界値関数は、初期条件関数が呼び出されるのと同じ引数で呼び出されます。すなわち、

```julia
boundary_normal_flux_function(x, t, equations)
```

ここで、`x`は座標を指定し、`t`は現在の時間、`equation`は対応する方程式系です。
