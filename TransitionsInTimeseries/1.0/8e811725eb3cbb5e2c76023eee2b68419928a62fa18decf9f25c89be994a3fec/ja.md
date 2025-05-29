```
plot_significance!(axs, res, signif)
```

`plot_indicator_changes(res)` で得られた図の `axs::Matrix{Axis}` を `signif::SurrogatesSignificance` で更新します。

## キーワード引数:

  * `flags = nothing` は、有意性フラグを提供します。例えば、p値をしきい値処理することで得られます。
  * `nsurro = 20` は、プロットするサロゲートの数を設定します。
