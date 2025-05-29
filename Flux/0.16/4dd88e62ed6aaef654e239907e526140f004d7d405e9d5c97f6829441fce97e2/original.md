```
f16(m)
```

Converts the `eltype` of model's *floating point* parameters to `Float16`. Recurses into structs marked with [`@layer`](@ref Flux.@layer).

Support for `Float16` is limited on many CPUs. Julia may convert to `Float32` for each operation, which is slow.

See also [`f32`](@ref) and [`f64`](@ref).

# Example

```jldoctest
julia> m = Chain(Dense(784, 2048, relu), Dense(2048, 10))  # all Float32
Chain(
  Dense(784 => 2048, relu),             # 1_607_680 parameters
  Dense(2048 => 10),                    # 20_490 parameters
)                   # Total: 4 arrays, 1_628_170 parameters, 6.211 MiB.

julia> m |> f16  # takes half the memory
Chain(
  Dense(784 => 2048, relu),             # 1_607_680 parameters
  Dense(2048 => 10),                    # 20_490 parameters
)                   # Total: 4 arrays, 1_628_170 parameters, 3.106 MiB.
```
