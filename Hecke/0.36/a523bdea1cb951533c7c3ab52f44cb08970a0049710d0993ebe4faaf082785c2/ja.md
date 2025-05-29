```
irreducible_components(L::ZZLat) -> Vector{ZZLat}
```

定義格 $L$ の不可約成分 $L_i$ を返します。

これは `L` の最大直交分割を生成します。

$$
L = \bigoplus_i L_i.
$$

分解は因子の順序を除いて一意です。

# 例

```jldoctest
julia> R = integer_lattice(; gram=2 * identity_matrix(ZZ, 24));

julia> N = maximal_even_lattice(R); # ニーメイヤー格

julia> irr_comp = irreducible_components(N)
3-element Vector{ZZLat}:
 ランク 8 および次数 24 の整数格
 ランク 8 および次数 24 の整数格
 ランク 8 および次数 24 の整数格

julia> genus.(irr_comp)
3-element Vector{ZZGenus}:
 属の記号: II_(8, 0)
 属の記号: II_(8, 0)
 属の記号: II_(8, 0)
```
