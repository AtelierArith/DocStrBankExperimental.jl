```
tile(s::AbstractScheme, A)
tile(s::AbstractExtendScheme, A)
```

`A`全体にスキーム`s`を適用することによって`Tile`を構築します。

`AbstractScheme`と`AbstractExtendScheme`の区別は、シグナル目的で存在します。`AbstractScheme`は常に基本ケースであり、`A`全体への適用を示します。一方、`ExtendScheme`は、`A`が最初にラップされているエンティティによって定義された内部インデックスに従ってパーティション分割されるべきであることを示します（`ExtendScheme(Scheme)`の場合は`e.s.g`、または`ExtendScheme(ExtendScheme(...))`の場合は`e.s.h`）、そして`Scheme`/`ExtendScheme`が各パーティションに適用されます。各パーティションは、`g`（または`h`）が同じ値を持つ連続した範囲で構成されているため、この値がパーティションのインデックスとして機能します。

参照: [`tiles`](@ref)

# 例

```jldoctest
julia> A = [10 1 1
            20 1 1
            30 1 1
            10 2 1
            20 2 1
            30 2 2
            10 3 2
            20 3 2
            10 4 2
            20 4 2];

julia> B = eachrow(A);

julia> s = @scheme sum x -> x[begin+1] last;


julia> x = tile(s, B)
4-element Tile{Vector{Tile{Vector{Int64}, Int64, Tuple{Int64}, Int64, 1}}, Tile{Vector{Int64}, Int64, Tuple{Int64}, Int64, 1}, Tuple{Int64}, Int64, 1}:
 [12, 22, 32]
 [13, 23, 34]
 [15, 25]
 [16, 26]
```
