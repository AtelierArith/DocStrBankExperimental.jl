```
brown_invariant(self::TorQuadModule) -> Nemo.zzModRingElem
```

このトーション二次形式のブラウン不変量を返します。

`(D,q)` を `Q / 2Z` の値を持つトーション二次モジュールとします。ブラウン不変量 `Br(D,q) in Z/8Z` は次の式によって定義されます。

$$
\exp \left( \frac{2 \pi i }{8} Br(q)\right) =
  \frac{1}{\sqrt{D}} \sum_{x \in D} \exp(i \pi q(x)).
$$

ブラウン不変量はトーション二次モジュールの直和に関して加法的です。

# 例

```jldoctest
julia> L = integer_lattice(gram=matrix(ZZ, [[2,-1,0,0],[-1,2,-1,-1],[0,-1,2,0],[0,-1,0,2]]));

julia> T = Hecke.discriminant_group(L);

julia> brown_invariant(T)
4
```
