```
Chain(layers...)
Chain(name = layer, ...)
```

Collects multiple layers / functions to be called in sequence on a given input. Supports indexing and slicing, `m[2]` or `m[1:end-1]`, and if names are given, `m[:name] == m[1]` etc.

# Examples

```jldoctest
julia> m = Chain(x -> x^2, x -> x+1);

julia> m(5) == 26
true

julia> m = Chain(Dense(10 => 5, tanh), Dense(5 => 2));

julia> x = rand32(10, 32);

julia> m(x) == m[2](m[1](x))
true

julia> m2 = Chain(enc = Chain(Flux.flatten, Dense(10 => 5, tanh)), 
                  dec = Dense(5 => 2));

julia> m2(x) == (m2[:dec] ∘ m2[:enc])(x)
true
```

A chain may be called with multiple arguments, which is equivalent to calling it with one tuple of these arguments. Such a tuple is understood by [`Parallel`](@ref) to mean the same as several arguments:

```jldoctest
julia> Chain(println, println)(1, 2, 3)  # three arguments become a tuple
(1, 2, 3)
nothing

julia> Chain(x->@show(x), Parallel(+, inv, abs2))(4, 5)  # returns 1/4 + 5^2
x = (4, 5)
25.25
```

For large models, there is a special type-unstable path which can reduce compilation times. This can be used by supplying a vector of layers `Chain([layer1, layer2, ...])`. This feature is somewhat experimental, beware!
