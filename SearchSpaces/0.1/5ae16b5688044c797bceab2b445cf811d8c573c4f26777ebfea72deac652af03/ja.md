```
A × B
```

直積を使用して混合空間を返します。

# 例

```julia-repl
julia> bounds = BoxConstrainedSpace(lb = zeros(Int, 5), ub = ones(Int, 5));

julia> permutations = PermutationSpace([:red, :green, :blue]);

julia> bits = BitArraySpace(3);

julia> mixed = bounds × permutations × bits
MixedSpace defined by 3 subspaces:
S3 => BitArraySpace(3)
S2 => PermutationSpace{Vector{Symbol}}([:red, :green, :blue], 3)
S1 => BoxConstrainedSpace{Int64}([0, 0, 0, 0, 0], [1, 1, 1, 1, 1], [1, 1, 1, 1, 1], 5, true)

julia> cardinality(mixed)
1536

julia> rand(mixed)
Dict{Symbol, Vector} with 3 entries:
  :S2 => [:red, :blue, :green]
  :S1 => [0, 1, 0, 0, 1]
  :S3 => Bool[1, 1, 0]
```
