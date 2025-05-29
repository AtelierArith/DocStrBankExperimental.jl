```
MixedSpace([itr])
```

検索空間を構築します。

# 例

```julia-repl
julia> space = MixedSpace( :X => BoxConstrainedSpace(lb = [-1.0, -3.0], ub = [10.0, 10.0]),
                          :Y => PermutationSpace(10),
                          :Z => BitArraySpace(dim = 10)
                          ) 
MixedSpaceは3つのサブスペースによって定義されています：
X => BoxConstrainedSpace{Float64}([-1.0, -3.0], [10.0, 10.0], [11.0, 13.0], 2, true)
Y => PermutationSpace{Vector{Int64}}([1, 2, 3, 4, 5, 6, 7, 8, 9, 10], 10)
Z => BitArraySpace(10)


julia> rand(space)
Dict{Symbol, Vector} with 3 entries:
  :Z => Bool[0, 1, 0, 0, 0, 0, 0, 1, 1, 0]
  :X => [0.367973, 4.62101]
  :Y => [4, 3, 9, 1, 7, 2, 10, 8, 5, 6]
```

詳細は [`×`](@ref) を参照してください。
