```
Grid(searchspace; npartitions)
```

与えられた検索空間に対するイテレータを返します。

`npartitions`は、`searchspace isa BoxConstrainedSpace`の場合に各軸のパーティション数を制御します（デフォルトは3です）。

# 例

```julia-repl
julia> for x in Grid(PermutationSpace([:red, :green, :blue]))
           @show x
       end
x = [:red, :green, :blue]
x = [:red, :blue, :green]
x = [:green, :red, :blue]
x = [:green, :blue, :red]
x = [:blue, :red, :green]
x = [:blue, :green, :red]

julia> for x in Grid(BoxConstrainedSpace(lb=[-1.0, -1], ub=[1, 0.0]), npartitions=3)
           @show x
       end
x = [-1.0, -1.0]
x = [0.0, -1.0]
x = [1.0, -1.0]
x = [-1.0, -0.5]
x = [0.0, -0.5]
x = [1.0, -0.5]
x = [-1.0, 0.0]
x = [0.0, 0.0]
x = [1.0, 0.0]

julia> mixed = MixedSpace(
                                 :W => CategorySpace([:red, :green, :blue]),
                                 :X => PermutationSpace(2),
                                 :Y => BitArrays(2),
                                );

julia> collect(Grid(mixed))
24-element Vector{Any}:
 Dict{Symbol, Any}(:W => :red, :X => [1, 2], :Y => Bool[0, 0])
 Dict{Symbol, Any}(:W => :green, :X => [1, 2], :Y => Bool[0, 0])
 Dict{Symbol, Any}(:W => :blue, :X => [1, 2], :Y => Bool[0, 0])
 Dict{Symbol, Any}(:W => :red, :X => [2, 1], :Y => Bool[0, 0])
 Dict{Symbol, Any}(:W => :green, :X => [2, 1], :Y => Bool[0, 0])
 Dict{Symbol, Any}(:W => :blue, :X => [2, 1], :Y => Bool[0, 0])
 ⋮
 Dict{Symbol, Any}(:W => :blue, :X => [2, 1], :Y => Bool[0, 1])
 Dict{Symbol, Any}(:W => :red, :X => [1, 2], :Y => Bool[1, 1])
 Dict{Symbol, Any}(:W => :green, :X => [1, 2], :Y => Bool[1, 1])
 Dict{Symbol, Any}(:W => :blue, :X => [1, 2], :Y => Bool[1, 1])
 Dict{Symbol, Any}(:W => :red, :X => [2, 1], :Y => Bool[1, 1])
 Dict{Symbol, Any}(:W => :green, :X => [2, 1], :Y => Bool[1, 1])
 Dict{Symbol, Any}(:W => :blue, :X => [2, 1], :Y => Bool[1, 1])
```
