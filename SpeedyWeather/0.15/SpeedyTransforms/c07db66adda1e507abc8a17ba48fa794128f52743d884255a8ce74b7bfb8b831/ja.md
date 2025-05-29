```julia
divergence(
    u::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    v::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    kwargs...
) -> SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray

```

二つのベクトル成分 `u, v` の発散 (∇⋅) は、サイズが (n+1)xn である必要があり、返される `LowerTriangularMatrix` の最終行はゼロに設定されます。この関数は、`u, v` の両方が `1/cos(lat)` でスケーリングされたフィールドの変換である必要があります。単位球体に作用し、`radius` キーワード引数が提供されない限り、1/radius スケーリングを省略します。したがって、使用例は次のようになります。

```
RingGrids.scale_coslat⁻¹!(u_grid)
RingGrids.scale_coslat⁻¹!(v_grid)
u = transform(u_grid, one_more_degree=true)
v = transform(v_grid, one_more_degree=true)
div = divergence(u, v, radius = 6.371e6)
div_grid = transform(div)
```
