```
coordinates(Function, las::LAS; crs)
```

`PointRecord`を引数として受け取り、その点の再スケーリングされた座標を返す関数を作成します。指定された`crs`がない限り、`las`の座標参照系（CRS）で返されます。

参照: [`LAS`](@ref), [`getcrs`](@ref)
