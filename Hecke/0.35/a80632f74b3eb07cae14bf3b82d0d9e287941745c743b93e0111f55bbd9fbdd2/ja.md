```
lll_gram_indef_isotropic(G::MatElem{ZZRingElem}, base::Bool = false)
                                                    -> MatElem{ZZRingElem},
                                                       MatElem{ZZRingElem},
                                                       MatElem{ZZRingElem}}
```

整数エントリを持つフルランク対称行列 `G` が与えられたとき、これは不定整数二次形式 `L` のグラム行列を定義します。`L` の同次ベクトルが見つかった場合、`G`、`I`（単位行列）、および `sol`（`L` の同次ベクトル）を返します。

`L` の同次ベクトルが見つからない場合、`L` の LLL縮約基底 `U` を計算し、`G`、LLL縮約基底行列 `U`、および空のベクトル `ZZRingElem[]` を返します。

`base` が `true` に設定されている場合、最初の出力は `U*G*transpose(U)` に置き換えられ、これは `U` に関する `L` のグラム行列です。

# 例

```jldoctest
julia> G = ZZ[0 1 2; 1 -1 3; 2 3 0];

julia> lll_gram_indef_isotropic(G)
([0 1 2; 1 -1 3; 2 3 0], [1 0 0; 0 1 0; 0 0 1], [1 0 0])

julia> (ans[3]*G*transpose(ans[3]))[1] == 0
true

julia> G = ZZ[2 1 2 4;1 8 0 2;2 0 -2 5;4 2 5 0];

julia> lll_gram_indef_isotropic(G)
([2 0 1 0; 0 -4 -1 1; 1 -1 8 0; 0 1 0 -8], [1 0 0 0; -1 0 1 0; 0 1 0 0; -2 0 0 1], ZZRingElem[])
```
