```
@init_fn(fn, kind::Symbol = :parameter)
```

Create an initializer function for a parameter or state to be used for in a Compact Lux Layer created using [`@compact`](@ref).

## Arguments

  * `fn`: The function to be used for initializing the parameter or state. This only takes a single argument `rng`.
  * `kind`: If set to `:parameter`, the initializer function will be used to initialize the parameters of the layer. If set to `:state`, the initializer function will be used to initialize the states of the layer.

## Examples

```jldoctest
julia> using Lux, Random

julia> r = @compact(w=@init_fn(rng->randn32(rng, 3, 2)),
           b=@init_fn(rng->randn32(rng, 3), :state)) do x
           @return w * x .+ b
       end;

julia> ps, st = Lux.setup(Xoshiro(0), r);

julia> size(ps.w)
(3, 2)

julia> size(st.b)
(3,)

julia> size(r([1, 2], ps, st)[1])
(3,)
```
