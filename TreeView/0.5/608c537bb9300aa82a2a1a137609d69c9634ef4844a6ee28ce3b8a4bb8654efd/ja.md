```jldoctest
julia> using TikzGraphs

julia> tree = Tree(g = Graph(3), labels = ["A", "B", "C"])
Tree{Int64} with 3 nodes:
  1: A
  2: B
  3: C

julia> TikzGraphs.tikz(tree)
```
