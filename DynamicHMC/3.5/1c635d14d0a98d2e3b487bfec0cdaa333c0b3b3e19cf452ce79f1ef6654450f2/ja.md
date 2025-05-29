```julia
pool_posterior_matrices(results)

```

`results`のベクトルを与えると、各要素には`posterior_matrix`プロパティが含まれています（例えば、同じサンプル長で[`mcmc_with_warmup`](@ref)から取得されたもの）。`[parameter_index, pooled_draw_index]`でインデックス付けされた配列として遅延ビューを返します。

これは、診断後の事後分析に役立ちます（例えば、`Base.eachcol`を参照）。
