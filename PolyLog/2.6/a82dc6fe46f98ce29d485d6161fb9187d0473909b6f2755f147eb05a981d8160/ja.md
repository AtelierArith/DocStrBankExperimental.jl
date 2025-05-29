```
reli(n::Integer, x::Real)
```

実数 $x$ の実数 n 次ポリログarithm $\Re[\operatorname{Li}_n(x)]$ をすべての整数 $n$ に対して返します。

$$
n < 0
$$

の場合の実装は [[arxiv:2010.09860](https://arxiv.org/abs/2010.09860)] の適応です。

著者: アレクサンダー・フォイヒト

ライセンス: MIT

# 例

```jldoctest; setup = :(using PolyLog)
julia> reli(10, 1.0)
1.0009945751278182

julia> reli(10, BigFloat("1.0"))
1.000994575127818085337145958900319017006019531564477517257788994636291465151908
```
