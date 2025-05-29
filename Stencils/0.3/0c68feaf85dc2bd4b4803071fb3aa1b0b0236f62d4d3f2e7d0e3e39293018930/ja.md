```
ForwardSlash <: Stencil

ForwardSlash(; radius=1, ndims=2)
ForwardSlash(radius, ndims)
ForwardSlash{R,N}()
```

「前方」対角線のみが含まれる近傍。`2:N` 次元のために `2R+1` の隣接点を含みます。
