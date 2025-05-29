```
TileCodingBasis(num_inputs::Int, num_tiles::Int; num_tilings::Int, tiling_type::Symbol=:wrap, tile_loc::Symbol=:equal)
```

`num_inputs` 入力と `num_tiles` タイルを持つタイルコーディング基底を作成します。 `num_tilings` は使用する異なるタイルの数を表します。 `tiling_type` は `:wrap` または `:clip` のいずれかで、タイルが入力空間の端でラップするか、端でクリップされるかを決定します。 `tile_loc` は `:equal` または `:random` のいずれかで、タイルが入力空間全体に均等に広がるか、ランダムに分布するかを決定します。あるいは、構築時に `num_tiles` を整数のベクトルとして指定し、入力ごとのタイル数を指定することもできます。タイルは各入力に対して [0,1] の範囲に均等に広がります。この基底はスパースベクトルとして実装されており、各要素は入力が対応するタイルにある場合は 1、そうでない場合は 0 です。

参照: [`FourierBasisBuffer`](@ref)

# 例

```jldoctest
julia> f = TileCodingBasis(2, 3, num_tilings=1, tiling_type=:wrap, tile_loc=:equal);

julia> x = [0.0, 0.0];

julia> feats = f(x)
(1,)

julia> feats = f([1,1])  # 1.0 の位置で入力が 0.0 にラップされる
(1,)

julia> feats = f([0.99,0.99]) 
(9,)

julia> length(f)
9

julia> size(f)
(9,1)

julia> f = TileCodingBasis([10,10,3], num_tilings=2);

julia> length(f)
600

julia> size(f)
(300,2)

julia> f([0.0, 0.0, 0.99])  # これは最初のタイルの最後の 100 タイルに含まれます
(201,1)

```
