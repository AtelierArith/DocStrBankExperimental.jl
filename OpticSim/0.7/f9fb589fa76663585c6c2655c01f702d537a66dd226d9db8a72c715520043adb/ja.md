```
Plane{T,N} <: ParametricSurface{T,N}
```

無限平面で、正の法線側は表面の外側です。

デフォルトでは、視覚化のためのジオメトリは作成されません。オプションの `vishalfsizeu` および `vishalfsizev` 引数を使用して、平面を視覚化のために長方形として描画できます **ただし、これは表面を完全には表現していないことに注意してください**。この場合、平面に対する法線の周りの長方形の回転は `visvec` によって定義されます - `surfacenormal×visvec` が u 軸に沿ったベクトルとして取られます。

```julia
Plane(surfacenormal::SVector{N,T}, pointonplane::SVector{N,T}; interface::NullOrFresnel{T} = nullinterface(T), vishalfsizeu::T = 0.0, vishalfsizev::T = 0.0, visvec::SVector{N,T} = [0.0, 1.0, 0.0])
Plane(nx::T, ny::T, nz::T, x::T, y::T, z::T; interface::NullOrFresnel{T} = nullinterface(T), vishalfsizeu::T = 0.0, vishalfsizev::T = 0.0, visvec::SVector{N,T} = [0.0, 1.0, 0.0])
```
