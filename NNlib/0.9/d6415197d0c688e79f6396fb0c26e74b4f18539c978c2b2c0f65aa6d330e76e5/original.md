```
tanh_fast(x)
```

This is a faster but slighly less accurate version of `tanh`.

Where Julia's `tanh` function has an error under 2 eps, this may be wrong by 5 eps, a reduction by less than one decimal digit. 

For `x::Float32` this is usually about 10 times faster, with a smaller speedup for `x::Float64`. For any other number types, it just calls `tanh`.

See also [`sigmoid_fast`](@ref).

```julia-repl
julia> tanh(0.5f0)
0.46211717f0

julia> tanh_fast(0.5f0)
0.46211714f0

julia> hard_tanh(0.5f0)
0.5f0
```
