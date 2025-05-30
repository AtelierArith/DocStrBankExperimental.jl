```
lc1, mvf1, lc2, mvf2 = example_moebius(p)
```

円柱とメビウスの帯のための2つの単体複体を作成し、それぞれに関連する多ベクトル場を定義します。

この関数は、レフシェッツ複体 `lc1` と `lc2`、および多ベクトル場 `mvf1` と `mvf2` を返します。両方の複体は、特性 `p` の体上にあります。正の素特性は有限体 GF(p) を使用し、ゼロ特性は有理数を与えます。

多ベクトル場は同じであり、ストリップの内部に次元1と2のそれぞれに1つの臨界セルがあります。境界は、`lc1` と `mvf1` のための2つの周期軌道、およびメビウスの場合の `lc2` と `mvf2` のための1つの周期軌道で構成されています。後者のケースは、例えば GF(2) と GF(7) のフィールドに対して異なる接続行列をもたらします。

# 例

```jldoctest
julia> lc1, mvf1, lc2, mvf2 = example_moebius(0);

julia> lc2p2 = lefschetz_gfp_conversion(lc2,2);

julia> lc2p7 = lefschetz_gfp_conversion(lc2,7);

julia> cmp2 = connection_matrix(lc2p2, mvf2);

julia> cmp7 = connection_matrix(lc2p7, mvf2);

julia> sparse_show(cmp2.matrix)
[0   0   0   0]
[0   0   0   1]
[0   0   0   0]
[0   0   0   0]

julia> sparse_show(cmp7.matrix)
[0   0   0   0]
[0   0   0   1]
[0   0   0   2]
[0   0   0   0]
```
