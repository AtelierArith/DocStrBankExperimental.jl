```
VonNeumann <: Stencil

VonNeumann(; radius=1, ndims=2)
VonNeumann(radius, ndims)
VonNeumann{R,N}()
```

中央のセルを含まないダイヤモンド型の近傍（2次元）。1次元では[`Moore`](@ref)と同じです。
