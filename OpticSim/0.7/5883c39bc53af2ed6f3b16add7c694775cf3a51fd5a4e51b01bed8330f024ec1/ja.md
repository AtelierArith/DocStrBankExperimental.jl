```
RectangularAperture(aphalfsizeu::T, aphalfsizev::T, surfacenormal::SVector{3,T}, centrepoint::SVector{3,T}; rotationvec::SVector{3,T} = [0.0, 1.0, 0.0])
```

平面に矩形の開口を作成します。すなわち、`InfiniteStop{T,RectangularStopShape}`です。矩形の法線周りの回転は`rotationvec`によって定義されます。`rotationvec×surfacenormal`はu軸に沿ったベクトルとして取られます。
