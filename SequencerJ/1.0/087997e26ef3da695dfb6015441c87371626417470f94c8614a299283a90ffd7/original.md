```
EMD(u::AbstractVector{T}, v::AbstractVector{T}) where {T <: Real}
```

Calculate the Earth Mover Distance (EMD) a.k.a the 1-Wasserstein distance between the two given vectors, accepting a default grid. `u` and `v` are treated as  weights on the grid. The default grid is equal to the first axis of `u` and `v`.

```@example 1
u = rand(10);
u .= u / sum(u);
sum(u)
```

`EMD` implements the Distances package convention of runnable types:

```@example 1
v = rand(10);
v .= v / sum(v);
d = EMD()(u,v)
```
