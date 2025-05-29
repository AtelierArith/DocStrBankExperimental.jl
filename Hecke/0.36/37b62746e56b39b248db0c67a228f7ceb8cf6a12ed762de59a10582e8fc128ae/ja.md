```
lll_gram_indef_ternary_hyperbolic(G::MatElem{ZZRingElem}; check::Bool = false)
                                                    -> MatElem{ZZRingElem},
                                                       MatElem{ZZRingElem}
```

整数エントリを持つフルランク対称行列 `G` が与えられたとき、これは非退化三項双曲線整数二次形式 `L` のグラム行列を定義します。`L` の LLL縮約基底 `U` を計算し、`G'` が `U` に関する `L` のグラム行列である `(G', U)` を返します。

# 例

```jldoctest
julia> G = ZZ[1 0 0; 0 4 3; 0 3 2];

julia> lll_gram_indef_ternary_hyperbolic(G)
([0 0 -1; 0 1 0; -1 0 0], [-1 -1 0; 0 0 -1; -2 -1 0])
```
