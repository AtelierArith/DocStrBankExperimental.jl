```
ForwardSlash <: Stencil

ForwardSlash(; radius=1, ndims=2)
ForwardSlash(radius, ndims)
ForwardSlash{R,N}()
```

A neighboorhood where only 'forward' diagonals are included. Contains `2R+1` neighbors for `2:N` dimensions
