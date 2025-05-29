```
Maxout(layers...)
Maxout(f, n_alts)
```

This contains a number of internal layers, each of which receives the same input. Its output is the elementwise maximum of the internal layers' outputs.

Instead of defining layers individually, you can provide a zero-argument function which constructs them, and the number to construct.

Maxout over linear dense layers satisfies the universal approximation theorem. See Goodfellow, Warde-Farley, Mirza, Courville & Bengio "Maxout Networks"  [https://arxiv.org/abs/1302.4389](https://arxiv.org/abs/1302.4389).

See also [`Parallel`](@ref) to reduce with other operators.

# Examples

```jldoctest
julia> m = Maxout(x -> abs2.(x), x -> x .* 3);

julia> m([-2 -1 0 1 2])
1×5 Matrix{Int64}:
 4  1  0  3  6

julia> m3 = Maxout(() -> Dense(5 => 7, tanh), 3)
Maxout(
  Dense(5 => 7, tanh),                  # 42 parameters
  Dense(5 => 7, tanh),                  # 42 parameters
  Dense(5 => 7, tanh),                  # 42 parameters
)                   # Total: 6 arrays, 126 parameters, 816 bytes.

julia> Flux.outputsize(m3, (5, 11))
(7, 11)
```
