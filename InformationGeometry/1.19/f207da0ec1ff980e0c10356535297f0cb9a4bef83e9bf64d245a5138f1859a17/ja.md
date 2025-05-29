```
PlaneCoordinates(PL::Plane, v::AbstractVector{<:Number})
```

2つの実数のタプルからn次元ベクトルを返します。これらは2D `Plane`の座標に対応しています。つまり、`PlanarCoordinates`は平面パラメータを周囲の空間に埋め込む機能を提供します。逆関数は[`DecomposeWRTPlane`](@ref)で与えられます。
