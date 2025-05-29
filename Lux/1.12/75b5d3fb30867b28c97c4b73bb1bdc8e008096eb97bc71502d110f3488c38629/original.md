```
ReverseSequence(dim = nothing)
```

Reverse the specified dimension `dims` of the passed array

## Arguments

  * `dim`: Dimension that need to be reversed. If `nothing`, for AbstractVector{T} it reverses itself (dimension 1), for other arrays, reverse the dimension `ndims(x) - 1`.

## Inputs

  * `x`: AbstractArray.

## Returns

  * AbstractArray with the same dimensions as the input
  * Empty `NamedTuple()`

## Example

```jldoctest
julia> model = ReverseSequence()
ReverseSequence{Nothing}(nothing)

julia> rng = Random.default_rng();
       Random.seed!(rng, 0);
       ps, st = Lux.setup(rng, model);
       x = [1.0, 2.0, 3.0];

julia> y, st_new = model(x, ps, st)
([3.0, 2.0, 1.0], NamedTuple())
```
