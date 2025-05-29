```
+(A::LinearMap, B::LinearMap)::LinearCombination
```

Construct a (lazy) representation of the sum/linear combination of the two operators. Sums of `LinearMap`/`LinearCombination` objects and `LinearMap`/`LinearCombination` objects are reduced to a single `LinearCombination`. In sums of `LinearMap`s and `AbstractMatrix`/`UniformScaling` objects, the latter get promoted to `LinearMap`s automatically.

# Examples

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> CS = LinearMap{Int}(cumsum, 3)::LinearMaps.FunctionMap;

julia> LinearMap(ones(Int, 3, 3)) + CS + I + rand(3, 3);
```
