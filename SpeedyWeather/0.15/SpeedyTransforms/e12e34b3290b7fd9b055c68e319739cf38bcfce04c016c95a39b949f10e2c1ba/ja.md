```julia
curl(
    u::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray,
    v::SpeedyWeather.LowerTriangularMatrices.LowerTriangularArray;
    kwargs...
) -> Any

```

二つのベクトル成分 `u, v` のカール (∇×) はサイズ (n+1)xn であり、返される `LowerTriangularMatrix` の最後の行はゼロに設定されます。この関数は、`u, v` の両方が `1/cos(lat)` でスケーリングされたフィールドの変換である必要があります。単位球に作用し、`radius` キーワード引数が提供されない限り、1/radius スケーリングを省略します。したがって、使用例は次のとおりです。

```
RingGrids.scale_coslat⁻¹!(u_grid)
RingGrids.scale_coslat⁻¹!(v_grid)
u = transform(u_grid)
v = transform(v_grid)
vor = curl(u, v, radius=6.371e6)
vor_grid = transform(div)
```
