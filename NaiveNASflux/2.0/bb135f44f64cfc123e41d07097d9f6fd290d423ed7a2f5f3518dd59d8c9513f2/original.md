```
LazyMutable
LazyMutable(m::AbstractMutableComp)
```

Lazy version of MutableLayer in the sense that it does not perform any mutations until invoked to perform a computation.

This reduces the need to garbage collect when multiple mutations might be applied to a vertex before evaluating the model.

Also useable for factory-like designs where the actual layers of a computation graph are not instantiated until the graph is used.

# Examples

```jldoctest
julia> using NaiveNASflux, Flux

julia> struct DenseConfig end

julia> lazy = LazyMutable(DenseConfig(), 2, 3);

julia> layer(lazy)
DenseConfig()

julia> function NaiveNASflux.dispatch!(m::LazyMutable, ::DenseConfig, x)
       m.mutable = Dense(nin(m)[1], nout(m), relu)
       return m.mutable(x)
       end;

julia> lazy(ones(Float32, 2, 5)) |> size
(3, 5)

julia> layer(lazy)
Dense(2 => 3, relu)  # 9 parameters
```
