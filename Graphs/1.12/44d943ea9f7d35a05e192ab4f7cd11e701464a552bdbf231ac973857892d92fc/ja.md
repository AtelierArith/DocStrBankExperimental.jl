```
neighborhood_dists(g, v, d, distmx=weights(g))
```

`d`以下の測地線距離にある各頂点を表すタプルのベクトルを返し、`v`からの距離を含みます。非負の距離は`distmx`で指定できます。

### オプション引数

  * `dir=:out`: `g`が有向の場合、この引数は考慮される辺の`v`に対する方向を指定します。可能な値: `:in`または`:out`。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> neighborhood_dists(g, 1, 3)
4-element Vector{Tuple{Int64, Int64}}:
 (1, 0)
 (2, 1)
 (3, 2)
 (4, 3)

julia> neighborhood_dists(g, 1, 3, [0 1 0 0 0; 0 0 1 0 0; 1 0 0 0.25 0; 0 0 0 0 0.25; 0 0 0 0.25 0])
5-element Vector{Tuple{Int64, Float64}}:
 (1, 0.0)
 (2, 1.0)
 (3, 2.0)
 (4, 2.25)
 (5, 2.5)

julia> neighborhood_dists(g, 4, 3)
2-element Vector{Tuple{Int64, Int64}}:
 (4, 0)
 (5, 1)

julia> neighborhood_dists(g, 4, 3, dir=:in)
5-element Vector{Tuple{Int64, Int64}}:
 (4, 0)
 (3, 1)
 (5, 1)
 (2, 2)
 (1, 3)
```
