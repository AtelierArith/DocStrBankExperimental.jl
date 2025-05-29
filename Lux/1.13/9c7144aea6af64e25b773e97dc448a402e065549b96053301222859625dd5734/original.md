```
Parallel(connection, layers...; name=nothing)
Parallel(connection; name=nothing, layers...)
Parallel(; connection, layers..., name=nothing)
```

Create a layer which passes an input to each path in `layers`, before reducing the output with `connection`.

## Arguments

  * `connection`: An `N`-argument function that is called after passing the input through each layer. If `connection = nothing`, we return a tuple `Parallel(nothing, f, g)(x, y) = (f(x), g(y))`
  * Layers can be specified in two formats:

      * A list of `N` Lux layers
      * Specified as `N` keyword arguments.

# Extended Help

## Inputs

  * `x`: If `x` is not a tuple, then return is computed as `connection([l(x) for l in layers]...)`. Else one is passed to each layer, thus `Parallel(+, f, g)(x, y) = f(x) + g(y)`.

## Returns

  * See the Inputs section for how the output is computed
  * Updated state of the `layers`

## Parameters

  * Parameters of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N` (naming changes if using the kwargs API)

## States

  * States of each `layer` wrapped in a NamedTuple with `fields = layer_1, layer_2, ..., layer_N` (naming changes if using the kwargs API)

See also [`SkipConnection`](@ref) which is `Parallel` with one identity.

## Example

```jldoctest
julia> model = Parallel(nothing, Dense(2, 1), Dense(2, 1))
Parallel(
    layer_1 = Dense(2 => 1),            # 3 parameters
    layer_2 = Dense(2 => 1),            # 3 parameters
)         # Total: 6 parameters,
          #        plus 0 states.

julia> using Random;
       rng = Random.seed!(123);
       ps, st = Lux.setup(rng, model);
       x1 = randn(rng, Float32, 2);
       x2 = randn(rng, Float32, 2);

julia> size.(first(model((x1, x2), ps, st)))
((1,), (1,))
```
