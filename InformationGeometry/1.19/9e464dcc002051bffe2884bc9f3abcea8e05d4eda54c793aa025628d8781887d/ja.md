```
DecomposeWRTPlane(PL::Plane, x::AbstractVector)
```

与えられた平面の要素である空間からのベクトルを取り、その平面基底に関する座標を返します。つまり、`DecomposeWRTPlane`は平面埋め込み関数[`PlanarCoordinates`](@ref)の逆です。
