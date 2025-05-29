```
plot_autocor(x::Vector, dt = 0.1, dt_max = 300.0;
             show_plot::Bool  = true,
             save_plot::Bool  = false,
             plot_png::String = "autocor.png")
```

データの自己相関をプロットします（例：実際の測定値 - 期待される測定値）。`σ` = 標準偏差 & `τ` = `x`のe^-1までの自己相関減衰を出力します。

**引数:**

  * `x`:         データベクトル
  * `dt`:        （オプション）測定時間ステップ [s]
  * `dt_max`:    （オプション）評価する最大時間ステップ [s]
  * `show_plot`: （オプション）trueの場合、`p1`を表示
  * `save_plot`: （オプション）trueの場合、`p1`を`plot_png`として保存
  * `plot_png`:  （オプション）保存するプロットファイル名（`.png`拡張子はオプション）

**戻り値:**

  * `p1`: `x`の自己相関のプロット
