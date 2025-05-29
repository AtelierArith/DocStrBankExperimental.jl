```
*(A::LinearMap, B::LinearMap)::CompositeMap
```

Construct a (lazy) representation of the product of the two operators. Products of `LinearMap`/`CompositeMap` objects and `LinearMap`/`CompositeMap` objects are reduced to a single `CompositeMap`. In products of `LinearMap`s and `AbstractMatrix`/`UniformScaling` objects, the latter get promoted to `LinearMap`s automatically.

# Examples

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> CS = LinearMap{Int}(cumsum, 3)::LinearMaps.FunctionMap;

julia> LinearMap(ones(Int, 3, 3)) * CS * I * rand(3, 3);
```
