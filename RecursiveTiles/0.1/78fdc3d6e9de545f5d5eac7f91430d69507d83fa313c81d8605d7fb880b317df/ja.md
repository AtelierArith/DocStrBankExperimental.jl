```
tiles(s::AbstractScheme, A)
tiles(s::AbstractExtendScheme, A)
```

`A`をインデックスに従って分割することによって1つ以上の`Tiles`を構築します（`AbstractScheme`の場合は`s.g`、`AbstractExtendScheme`の場合は`s.h`）、その後、各分割`B`に対して`tile(s, B)`を呼び出します。インデックスを持つタイルのベクターを返します。

参照: [`tile`](@ref)

# 例

```jldoctest
julia> A = reshape(-12:12, 5, 5); B = eachcol(A);

julia> s = @scheme sum signbit ∘ (x -> x[begin+2]);

julia> tiles(s, B)
2-element Vector{Tile{Vector{Int64}, Int64, Tuple{Bool}, Bool, 1}}:
 [-50, -25]
 [0, 25, 50]
```
