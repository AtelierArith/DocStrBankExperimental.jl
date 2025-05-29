```
FromFluxAdaptor(preserve_ps_st::Bool=false, force_preserve::Bool=false)
```

Convert a Flux Model to Lux Model.

!!! warning "`active` field"
    This always ignores the `active` field of some of the Flux layers. This is almost never going to be supported.


## Keyword Arguments

  * `preserve_ps_st`: Set to `true` to preserve the states and parameters of the layer. This attempts the best possible way to preserve the original model. But it might fail. If you need to override possible failures, set `force_preserve` to `true`.
  * `force_preserve`: Some of the transformations with state and parameters preservation haven't been implemented yet, in these cases, if `force_transform` is `false` a warning will be printed and a core Lux layer will be returned. Else, it will create a [`FluxLayer`](@ref).

## Example

```julia
julia> import Flux

julia> using Adapt, Lux, Random

julia> m = Flux.Chain(Flux.Dense(2 => 3, relu), Flux.Dense(3 => 2));

julia> m2 = adapt(FromFluxAdaptor(), m); # or FromFluxAdaptor()(m.layers)

julia> x = randn(Float32, 2, 32);

julia> ps, st = Lux.setup(Random.default_rng(), m2);

julia> size(first(m2(x, ps, st)))
(2, 32)
```
