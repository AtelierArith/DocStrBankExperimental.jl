```
BackSlash <: Stencil

BackSlash(; radius=1, ndims=2)
BackSlash(radius, ndims)
BackSlash{R,N}()
```

'逆'対角線に沿った近傍。`2:N` 次元のために `2R+1` の隣接点を含みます。
