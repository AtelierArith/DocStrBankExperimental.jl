```
permute(T::ITensor, inds...; allow_alias = false)
```

Return a new ITensor `T` with indices permuted according to the input indices `inds`. The storage of the ITensor is permuted accordingly.

If called with `allow_alias = true`, it avoids copying data if possible. Therefore, it may return an alias of the input ITensor (an ITensor that shares the same data), such as if the permutation turns out to be trivial.

By default, `allow_alias = false`, and it never returns an alias of the input ITensor.

# Examples

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
