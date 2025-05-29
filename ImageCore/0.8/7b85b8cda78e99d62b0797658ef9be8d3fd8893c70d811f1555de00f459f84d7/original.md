```
colorview(C)
```

Create a function that is equivalent to `(As...) -> colorview(C, Ax...)`.

# Examples

```jldoctest; setup = :(using ImageCore)
julia> ones(Float32, 2, 2) |> colorview(Gray)
2×2 reinterpret(reshape, Gray{Float32}, ::Matrix{Float32}) with eltype Gray{Float32}:
 Gray{Float32}(1.0)  Gray{Float32}(1.0)
 Gray{Float32}(1.0)  Gray{Float32}(1.0)
```

This can be slightly convenient when you want to convert a batch of channel data, for example:

```julia
julia> Rs, Gs, Bs = ntuple( i -> [randn(2, 2) for _ in 1:4], 3)

julia> map(colorview(RGB), Rs, Gs, Bs)
```
