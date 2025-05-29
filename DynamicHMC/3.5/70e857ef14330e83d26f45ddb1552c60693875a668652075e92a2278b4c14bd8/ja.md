```julia
stack_posterior_matrices(results)

```

`results`のベクターを与えると、各要素には`posterior_matrix`プロパティが含まれています（例えば、同じサンプル長で[`mcmc_with_warmup`](@ref)から取得されたもの）。`[draw_index, chain_index, parameter_index]`でインデックス付けされた配列として遅延ビューを返します。

これは、例えば`MCMCDiagnosticTools.ess_rhat`の入力として便利です。

!!! note
    この順序は、MCMCDiagnostictoolsのバージョン< 0.2とは互換性がありません。

