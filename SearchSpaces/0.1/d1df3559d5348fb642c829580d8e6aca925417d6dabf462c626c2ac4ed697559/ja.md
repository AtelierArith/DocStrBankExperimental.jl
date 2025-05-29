```
cardinality(searchspace)
```

探索空間の基数。

# 例

```julia-repl
julia> cardinality(PermutationSpace(5))
120

julia> cardinality(BoxConstrainedSpace(lb = zeros(2), ub = ones(2)))
Inf

julia> cardinality(BoxConstrainedSpace(lb = zeros(Int, 2), ub = ones(Int,2)))
4

julia> mixed = MixedSpace(
                          :W => CategorySpace([:red, :green, :blue]),
                          :X => PermutationSpace(3),
                          :Y => BitArraySpace(3),
                         );

julia> cardinality(mixed)
144
```
