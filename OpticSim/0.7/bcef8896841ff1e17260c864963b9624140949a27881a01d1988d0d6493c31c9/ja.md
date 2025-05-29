```
RectangularAperture(innerhalfsizeu::T, innerhalfsizev::T, outerhalfsizeu::T, outerhalfsizev::T, surfacenormal::SVector{3,T}, centrepoint::SVector{3,T}; rotationvec::SVector{3,T} = [0.0, 1.0, 0.0])
```

長方形の開口部を長方形に作成します。すなわち、`FiniteStop{T,RectangularStopShape,RectangularStopShape}`。長方形の法線周りの回転は`rotationvec`によって定義されます。`rotationvec×surfacenormal`はu軸に沿ったベクトルとして取られます。
