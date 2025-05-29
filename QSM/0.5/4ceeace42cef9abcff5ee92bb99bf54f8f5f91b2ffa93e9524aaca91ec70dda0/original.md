```
homodyne!(
    v::AbstractArray{<:Complex{<:AbstractFloat}, N},
    u::AbstractArray{<:Complex{<:AbstractFloat}, N},
    w::AbstractArray{<:AbstractFloat, M <= N},
) -> v
```

Homodyne filter.

Filter by applying Md window to k-space of complex data: `v = u / F^-1(w * F(u))`.

### Arguments

  * `v::AbstractArray{<:Complex{<:AbstractFloat}, N}`:   homodyne filtered complex (multi-echo) data
  * `u::AbstractArray{<:Complex{<:AbstractFloat}, N}`:   complex (multi-echo) data
  * `w::AbstractArray{<:AbstractFloat, M <= N}`: k-space window centered at index `1`.

### Returns

  * `v`: homodyne filtered complex (multi-echo) data
