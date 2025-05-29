```
permute(T::ITensor, inds...; allow_alias = false)
```

入力インデックス `inds` に従ってインデックスが置換された新しい ITensor `T` を返します。ITensor のストレージもそれに応じて置換されます。

`allow_alias = true` で呼び出された場合、可能な限りデータのコピーを避けます。したがって、置換が自明である場合など、入力 ITensor のエイリアス（同じデータを共有する ITensor）を返すことがあります。

デフォルトでは、`allow_alias = false` であり、入力 ITensor のエイリアスを返すことはありません。

# 例

```julia
i = Index(2, "index_i"); j = Index(4, "index_j"); k = Index(3, "index_k");
T = random_itensor(i, j, k)

pT_1 = permute(T, k, i, j)
pT_2 = permute(T, j, i, k)

pT_noalias_1 = permute(T, i, j, k)
pT_noalias_1[1, 1, 1] = 12
T[1, 1, 1] != pT_noalias_1[1, 1, 1]

pT_noalias_2 = permute(T, i, j, k; allow_alias = false)
pT_noalias_2[1, 1, 1] = 12
T[1, 1, 1] != pT_noalias_1[1, 1, 1]

pT_alias = permute(T, i, j, k; allow_alias = true)
pT_alias[1, 1, 1] = 12
T[1, 1, 1] == pT_alias[1, 1, 1]
```
