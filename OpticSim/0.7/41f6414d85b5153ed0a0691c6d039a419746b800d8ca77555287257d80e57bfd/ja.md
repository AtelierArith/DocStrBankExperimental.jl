```
ConvexPolygon{N, T<:Real} <: PlanarShape{T}
```

一般的な凸多角形の表面であり、有効なCSGオブジェクトではありません。多角形の法線周りの回転は`rotationvec`によって定義されます。`rotationvec×surfacenormal`はu軸に沿ったベクトルとして取られます。

```julia
ConvexPolygon(local_frame::Transform{T}, local_polygon_points::Vector{SVector{2, T}}, interface::NullOrFresnel{T} = nullinterface(T))
```

ローカルフレームは、平面の定義（右ベクトルと上ベクトルによって張られる）を行い、平面の法線は前方ベクトルによって与えられます。local*polygon*pointsはローカルフレームに対して与えられ、2Dポイントです。注意：このクラスはポイントを保持するために静的ベクトルを使用しており、より効率的なパフォーマンスを実現しますが、20〜30ポイントを超える多角形には使用すべきではありません。
