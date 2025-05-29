```
neighborhood(g, v, d, distmx=weights(g); dir=:out)
```

`g`の各頂点で、距離が`d`以下の測地線距離を持つベクトルを返します。距離は`distmx`で指定できます。

### オプション引数

  * `dir=:out`: `g`が有向グラフの場合、この引数は考慮される辺の方向を`v`に対して指定します。可能な値: `:in`または`:out`。

# 例

```jldoctest
julia> g = DiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> neighborhood(g, 1, 2)
3-element Array{Int64,1}:
 1
 2
 3

julia> neighborhood(g, 1, 3)
4-element Array{Int64,1}:
 1
 2
 3
 4

julia> neighborhood(g, 1, 3, [0 1 0 0 0; 0 0 1 0 0; 1 0 0 0.25 0; 0 0 0 0 0.25; 0 0 0 0.25 0])
5-element Array{Int64,1}:
 1
 2
 3
 4
 5
```
