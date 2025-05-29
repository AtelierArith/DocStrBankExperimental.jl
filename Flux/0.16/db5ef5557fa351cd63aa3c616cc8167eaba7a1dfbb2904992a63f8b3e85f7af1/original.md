```
outputsize(m, x_size, y_size, ...; padbatch=false)
```

For model or layer `m` accepting multiple arrays as input, this returns `size(m((x, y, ...)))` given `size_x = size(x)`, etc.

# Examples

```jldoctest
julia> x, y = rand(Float32, 5, 64), rand(Float32, 7, 64);

julia> par = Parallel(vcat, Dense(5 => 9), Dense(7 => 11));

julia> Flux.outputsize(par, (5, 64), (7, 64))
(20, 64)

julia> m = Chain(par, Dense(20 => 13), softmax);

julia> Flux.outputsize(m, (5,), (7,); padbatch=true)
(13, 1)

julia> par(x, y) == par((x, y)) == Chain(par, identity)((x, y))
true
```

Notice that `Chain` only accepts multiple arrays as a tuple, while `Parallel` also accepts them as multiple arguments; `outputsize` always supplies the tuple.
