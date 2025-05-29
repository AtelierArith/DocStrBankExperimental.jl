```
ReshapeLayer(dims)
```

Reshapes the passed array to have a size of `(dims..., :)`

## Arguments

  * `dims`: The new dimensions of the array (excluding the last dimension).

## Inputs

  * `x`: AbstractArray of any shape which can be reshaped in `(dims..., size(x, ndims(x)))`

## Returns

  * AbstractArray of size `(dims..., size(x, ndims(x)))`
  * Empty `NamedTuple()`

## Example

```jldoctest
julia> model = ReshapeLayer((2, 2))
ReshapeLayer(output_dims = (2, 2, :))

julia> rng = Random.default_rng();
       Random.seed!(rng, 0);
       ps, st = Lux.setup(rng, model);
       x = randn(rng, Float32, (4, 1, 3));

julia> y, st_new = model(x, ps, st);
       size(y)
(2, 2, 3)
```
