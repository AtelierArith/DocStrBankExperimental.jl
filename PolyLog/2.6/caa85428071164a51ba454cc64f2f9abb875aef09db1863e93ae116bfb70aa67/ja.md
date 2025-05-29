```
reli2(x::Real)
```

実数 $x$ の実数二重対数 $\Re[\operatorname{Li}_2(x)]$ を返します。$x$ の型が `Real` です。

$$
x
$$

の型が `Float16`、`Float32` または `Float64` の場合、実装は [[arXiv:2201.01678](https://arxiv.org/abs/2201.01678)] の適応です。

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using PolyLog)
julia> reli2(1.0)
1.6449340668482264

julia> reli2(BigFloat("1.0"))
1.644934066848226436472415166646025189218949901206798437735558229370007470403202
```
