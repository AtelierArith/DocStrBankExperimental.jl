```
RecursiveOfType(out::Type, [optic=Children()]; [recurse::Type=Any])
```

Optic that references all values of type `out` located arbitrarily deep.

Recurses into values of type `recurse` (`Any` by default) using the specified inner `optic`. The default of `Children()` descends into all properties of objects, or into all elements of a collection.

___Note:___ typically, when changing the `optic` parameter, the `recurse` type should be narrowed as well.

## Examples

```julia
julia> obj = ([1,2,3], (a=[4,5], b=[6], c=([7], [8,9])));

# extract all numbers from the object:
julia> getall(obj, RecursiveOfType(Number))
9-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
 7
 8
 9

# extract the first element of each vector:
julia> getall(obj, @o _ |> RecursiveOfType(Vector) |> first)
(1, 4, 6, 7, 8)

# negate the first element of each vector:
julia> modify(x -> -x, obj, @o _ |> RecursiveOfType(Vector) |> first)
([-1, 2, 3], (a = [-4, 5], b = [-6], c = ([-7], [-8, 9])))
```
