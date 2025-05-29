```
plot_activation(activation = [:relu,:σ,:swish,:tanh];
                plot_deriv::Bool  = false,
                show_plot::Bool   = true,
                save_plot::Bool   = false,
                plot_png::String  = "act_func.png")
```

活性化関数またはその導関数をプロットします。

**引数:**

  * `activation`: プロットする活性化関数

      * `relu`  = 修正線形単位
      * `σ`     = シグモイド（ロジスティック関数）
      * `swish` = セルフゲーテッド
      * `tanh`  = 双曲線タンジェント
  * `plot_deriv`: （オプション）trueの場合、活性化関数の導関数をプロット
  * `show_plot`:  （オプション）trueの場合、`p1`を表示
  * `save_plot`:  （オプション）trueの場合、`p1`を`plot_png`として保存
  * `plot_png`:   （オプション）保存するプロットファイル名（`.png`拡張子はオプション）

**戻り値:**

  * `p1`: 活性化関数またはその導関数のプロット
