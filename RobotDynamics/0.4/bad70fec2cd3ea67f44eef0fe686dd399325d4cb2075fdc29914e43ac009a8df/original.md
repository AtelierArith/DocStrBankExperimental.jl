```
KnotPoint{Nx,Nu,V,T}
```

A mutable [`AbstractKnotPoint`](@ref) with `Nx` states, `Nu` controls, stored using  a vector type `V` with data type `T`. Since the struct is mutable, the time, timestep,  and data can all be changed, which can be very efficient when the data being stored  as an `SVector`.

# Constructors

```
KnotPoint{n,m}(v, t, dt)
KnotPoint{n,m}(x, u, t, dt)
KnotPoint{n,m}(n, m, v, t, dt) 
KnotPoint(n, m, v, t, dt)       # create a KnotPoint{Any,Any}
KnotPoint(x, u, t, dt)
```

The last method will create a `KnotPoint{Any,Any}` if `x` and `u` are not `StaticVector`s.

The vector type `V` can be queried using `vectype(z)`.
