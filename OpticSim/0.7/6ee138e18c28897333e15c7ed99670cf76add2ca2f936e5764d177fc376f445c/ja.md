```
Cylinder{T,N} <: ParametricSurface{T,N}
```

原点を中心とし、z軸に沿って向けられた無限の高さの円柱。`visheight`は視覚化の目的でのみ使用され、**これは表面を完全に表すものではないことに注意してください**。

```julia
Cylinder(radius::T, visheight::T = 2.0; interface::NullOrFresnel{T} = nullinterface(T))
```
