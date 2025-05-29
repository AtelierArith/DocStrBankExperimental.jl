```
n_components(V::Vector{T}, D::Dict{Tuple{T, T}, Bool})
```

出力は、頂点 V とエッジ D によって与えられるグラフの連結成分を表す配列です（より正確には、エッジは D のキーによって与えられ、そのエントリが「true」であるものです）。

# 例

julia> V = [1, 2, 3, 4];

julia> D = Dict{Tuple{Int, Int}, Bool}((1, 2) => true, (3, 4) => true, (2, 3) => false);

julia> components(V, D) 2-element Vector{Vector{Int64}}:  [1, 2]  [3, 4] ```
