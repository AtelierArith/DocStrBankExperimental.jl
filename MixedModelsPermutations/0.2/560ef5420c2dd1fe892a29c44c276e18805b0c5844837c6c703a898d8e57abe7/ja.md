```
permutationtest(perm::MixedModelPermutation, model, type=:greater)
```

既に計算された置換と与えられた観測値を使用して置換を実行します。

`type` パラメータは、二項検定（`:twosided`）の使用または片側検定の方向性（仮定された差に応じて `:lesser` または `:greater`）を指定します。

詳細は [`permutation`](@ref) を参照してください。

有限置換を考慮するために、Phipson & Smyth 2010 の保守的な方法を実装しました: Permutation P-values Should Never Be Zero: Calculating Exact P-values When Permutations Are Randomly Drawn  http://www.statsci.org/webguide/smyth/pubs/permp.pdf
