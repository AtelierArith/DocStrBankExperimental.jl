```
destruct(v::Array{<:Tuple,N})
```

Destructure an array of tuples to a tuple of arrays. Works for tuples with elements of varying types.

## Examples

```julia-repl
julia> f(a, b) = a+b, a*b, a-b;
julia> v = f.(rand(3,1), rand(1,4));
julia> x, y, z = destruct(v);
julia> x
3×4 Array{Float64,2}:
 0.301013  0.888299  1.03866  1.0867
 0.853248  1.44053   1.5909   1.63894
 0.687546  1.27483   1.4252   1.47324
julia> v = f.(rand(100,1,1), rand(1,100,100));
julia> @btime destruct(v);
  7.138 ms (7 allocations: 22.89 MiB)
julia> x, y, z = f.(rand(100,1,1), rand(1,100,100)) |> destruct;
```
