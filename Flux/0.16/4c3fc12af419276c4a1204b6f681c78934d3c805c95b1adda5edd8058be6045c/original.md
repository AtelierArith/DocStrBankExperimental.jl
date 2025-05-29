```
outputsize(m, inputsize::Tuple; padbatch=false)
```

Calculate the size of the output from model `m`, given the size of the input. Obeys `outputsize(m, size(x)) == size(m(x))` for valid input `x`.

Keyword `padbatch=true` is equivalent to using `(inputsize..., 1)`, and returns the final size including this extra batch dimension.

This should be faster than calling `size(m(x))`. It uses a trivial number type, which should work out of the box for custom layers.

If `m` is a `Tuple` or `Vector`, its elements are applied in sequence, like `Chain(m...)`.

# Examples

```jldoctest
julia> using Flux: outputsize

julia> outputsize(Dense(10 => 4), (10,); padbatch=true)
(4, 1)

julia> m = Chain(Conv((3, 3), 3 => 16), Conv((3, 3), 16 => 32));

julia> m(randn(Float32, 10, 10, 3, 64)) |> size
(6, 6, 32, 64)

julia> outputsize(m, (10, 10, 3); padbatch=true)
(6, 6, 32, 1)

julia> outputsize(m, (10, 10, 3, 64))
(6, 6, 32, 64)

julia> try outputsize(m, (10, 10, 7, 64)) catch e println(e) end
DimensionMismatch("layer Conv((3, 3), 3 => 16) expects size(input, 3) == 3, but got 10×10×7×64 Array{Flux.NilNumber.Nil, 4}")

julia> outputsize([Dense(10 => 4), Dense(4 => 2)], (10, 1)) # Vector of layers becomes a Chain
(2, 1)
```
