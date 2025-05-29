```
FlattenLayer(; N = nothing)
```

Flattens the passed array into a matrix.

## Keyword Arguments

  * `N`: Flatten the first `N` dimensions of the input array. If `nothing`, then all dimensions (except the last) are flattened. Note that the batch dimension is never flattened.

## Inputs

  * `x`: AbstractArray

## Returns

  * AbstractMatrix of size `(:, size(x, ndims(x)))` if `N` is `nothing` else the first `N` dimensions of the input array are flattened.
  * Empty `NamedTuple()`

## Example

```jldoctest
julia> model = FlattenLayer()
FlattenLayer{Nothing}(nothing)

julia> rng = Random.default_rng();
       Random.seed!(rng, 0);
       ps, st = Lux.setup(rng, model);
       x = randn(rng, Float32, (2, 2, 2, 2));

julia> y, st_new = model(x, ps, st);
       size(y)
(8, 2)
```
