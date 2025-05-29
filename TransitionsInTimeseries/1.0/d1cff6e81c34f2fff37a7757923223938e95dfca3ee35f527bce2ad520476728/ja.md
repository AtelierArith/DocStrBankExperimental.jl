```
plot_indicator_changes(res) → (fig, axs)
```

`fig::Figure` と `axs::Matrix{Axis}` を返します。ここで、`res::ChangesResults` が視覚化されています。

## キーワード引数:

  * `colors = default_colors` は、循環するラインプロットの色を設定します。デフォルトは Julia Dynamics のカラースキームに対応しています。
  * `indicator*names = default*indicator*label(res), chametric*names = default*chametric*label(res)` は、指標と変化メトリックのラベルを設定します。デフォルトは `res.config.indicators` と `res.config.change_metrics` の名前から推測されます。
  * `accent_linewidth = 3` は、元の信号のライン幅を設定します（サロゲートは `linewidth = 1` です）。
