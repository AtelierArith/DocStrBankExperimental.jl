```
UniquePoints{T, Id, M}
```

A data structure for assessing quickly whether a point is close to an indexed point as determined by the given distance function `M`.  The indexed points are only stored by their identifiers `Id`.  `triangle_inequality` should be set to `true`, if the distance function satisfies the triangle inequality.  Otherwise, it should be set to `false`. If `triangle_inequality` is nothing the algorithm will try to detect whether the triangle is satisfied.

```
UniquePoints(v::AbstractVector{T}, id::Id;
                distance = EuclideanNorm(),
                triangle_inequality = nothing,
                group_actions = nothing)
```

Initialize the data structure. This *does not* initialize the data structure with the point.

## Example

```julia
x = randn(ComplexF64, 4)
permutation(x) = ([x[2]; x[1]; x[3]; x[4]],)
group_actions = GroupActions(permutation)
X = group_actions(x)

# without group actions
unique_points = UniquePoints(x, 1)
HC.add!.(unique_points, X, 1:length(X), 1e-5)
length(unique_points) # 2

unique_points = UniquePoints(x, 1, group_actions = group_actions)
HC.add!.(unique_points, X, 1:length(X), 1e-5)
length(unique_points) # 1
```
