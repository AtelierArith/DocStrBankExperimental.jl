```
Scale(size::Integer..., σ=identity; bias=true, init=ones32)
Scale(scale::AbstractArray, [bias, σ])
```

Create an element-wise layer, whose forward pass is given by:

```
y = σ.(scale .* x .+ bias)
```

This uses `.*` instead of matrix multiplication `*` of [`Dense`](@ref).

The learnable scale & bias are initialised `init(size...)` and `zeros32(size...)`, with `init=ones32` by default. You may specify the function `init`,  turn off trainable bias with `bias=false`, or provide the array(s) explicitly.

Used by [`LayerNorm`](@ref) with `affine=true`.

# Examples

```jldoctest
julia> a = Flux.Scale(2)
Scale(2)            # 4 parameters

julia> Flux.trainables(a)
2-element Vector{AbstractArray}:
 Float32[1.0, 1.0]
 Float32[0.0, 0.0]

julia> a([1 2 3])
2×3 Matrix{Float32}:
 1.0  2.0  3.0
 1.0  2.0  3.0

julia> b = Flux.Scale(Float32[1 2 3 4], false, abs2)
Scale(1, 4, abs2; bias=false)  # 4 parameters

julia> b([1, 10])
2×4 Matrix{Float32}:
   1.0    4.0    9.0    16.0
 100.0  400.0  900.0  1600.0

julia> Flux.trainables(b)
1-element Vector{AbstractArray}:
 Float32[1.0 2.0 3.0 4.0]
```
