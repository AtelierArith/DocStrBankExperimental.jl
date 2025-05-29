```
lll_gram_indef_with_transform(G::MatElem{ZZRingElem}; check::Bool = false)
                                                    -> MatElem{ZZRingElem},
                                                       MatElem{ZZRingElem}
```

整数エントリを持つフルランク対称行列 `G` が与えられたとき、これは非退化の不定整数二次形式 `L` のグラム行列を定義します。`L` の LLL縮約基底 `U` を計算し、`G'` が `U` に関する `L` のグラム行列である `(G', U)` を返します。

注意: `G` がユニモジュラーでない場合、アルゴリズムは最終的に複数回適用される必要があります。

# 例

```jldoctest
julia> G = ZZ[0 1 2; 1 -1 3; 2 3 0];

julia> lll_gram_indef_with_transform(G)
([0 0 1; 0 -16 0; 1 0 1], [1 0 0; 5 2 -1; 1 1 0])

julia> G = ZZ[2 1 2 4;1 8 0 2;2 0 -2 5;4 2 5 0];

julia> lll_gram_indef_with_transform(G)
([2 0 1 0; 0 -4 -1 1; 1 -1 8 0; 0 1 0 -8], [1 0 0 0; -1 0 1 0; 0 1 0 0; -2 0 0 1])
```
