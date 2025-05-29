```
GeoArray{T::NumberOrMissing,N,A<:AbstractArray{T,N}} <: AbstractArray{T,N}
```

GeoArrayはAbstractArrayであり、軸に基づいて座標を計算するためのAffineMapと、これらの座標を現実世界で解釈するためのCRS定義を持っています。これは三次元であり、2D地理空間ラスタ（バンド）のスタック（3D）として見ることができ、次元は:x、:y、および:bandsです。AffineMapとCRS（座標）は、:xおよび:y次元のみに作用します。
