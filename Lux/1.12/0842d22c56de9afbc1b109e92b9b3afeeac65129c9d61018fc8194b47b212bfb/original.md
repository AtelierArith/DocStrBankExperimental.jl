```
ToSimpleChainsAdaptor(input_dims, convert_to_array::Bool=false)
```

Adaptor for converting a Lux Model to SimpleChains. The returned model is still a Lux model, and satisfies the `AbstractLuxLayer` interfacem but all internal calculations are performed using SimpleChains.

!!! warning
    There is no way to preserve trained parameters and states when converting to `SimpleChains.jl`.


!!! warning
    Any kind of initialization function is not preserved when converting to `SimpleChains.jl`.


## Arguments

  * `input_dims`: Tuple of input dimensions excluding the batch dimension. These must be of `static` type as `SimpleChains` expects.
  * `convert_to_array`: SimpleChains.jl by default outputs `StrideArraysCore.StrideArray`, but this might not compose well with other packages. If `convert_to_array` is set to `true`, the output will be converted to a regular `Array`.

## Example

```jldoctest
julia> import SimpleChains

julia> using Adapt, Lux, Random

julia> lux_model = Chain(Conv((5, 5), 1 => 6, relu), MaxPool((2, 2)),
           Conv((5, 5), 6 => 16, relu), MaxPool((2, 2)), FlattenLayer(3),
           Chain(Dense(256 => 128, relu), Dense(128 => 84, relu), Dense(84 => 10)));

julia> adaptor = ToSimpleChainsAdaptor((28, 28, 1));

julia> simple_chains_model = adapt(adaptor, lux_model); # or adaptor(lux_model)

julia> ps, st = Lux.setup(Random.default_rng(), simple_chains_model);

julia> x = randn(Float32, 28, 28, 1, 1);

julia> size(first(simple_chains_model(x, ps, st)))
(10, 1)
```
