```
OddEvenAsphericSurface(semidiameter, curvature::T, conic::T, aspherics::Vector{T}; normradius::T=semidiameter)
```

非球面多項式を組み込んだ表面 - 半径、円錐曲率および非球面項は絶対半径に対して定義されます。

`aspherics` は、A1から始まる非球面多項式の奇数および偶数係数の配列である必要があります。
