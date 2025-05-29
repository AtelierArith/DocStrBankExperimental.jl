```
TileCodingModel([::Type,] ϕ; num_tiles, num_tilings, num_outputs=1, num_actions=1)
```

ϕがタイルコーディング基底関数であると仮定し、各タイルのタイルを表す整数または整数のタプル/リストを返す線形関数を作成します。この構造体は複数の出力（num*outputs > 1）とアクション条件付き予測（num*actions > 1）をサポートします。TabularModelは、アイデンティティ基底関数を使用し、1つのタイルとタイルの数が状態の数に等しいタイルコーディングモデルの特別なケースでもあります。

参照: [`TabularModel`](@ref), [`LinearModel`](@ref)

# 例

```jldoctest
julia> ϕ = TileCodingBasis(1, 3, num_tilings=1, tiling_type=:clip, tile_loc=:equal);

julia> num_tiles, num_tilings = size(ϕ);

julia> m = TileCodingModel(ϕ, num_tiles=num_tiles, num_tilings=num_tilings);

julia> vec(params(m)) .= 1:length(params(m));

julia> [m(i) for i in [0.0, 0.5, 1.0]]
3-element Vector{Float64}:
 1.0
 2.0
 3.0

julia> v, g = value_withgrad(m, 0.5);

julia> v
2.0

julia> g  # アクティブなタイルのみが非ゼロの勾配を持つ
1×3×1×1 Array{Float64, 4}:
[:, :, 1, 1] =
 0.0  1.0  0.0

```
