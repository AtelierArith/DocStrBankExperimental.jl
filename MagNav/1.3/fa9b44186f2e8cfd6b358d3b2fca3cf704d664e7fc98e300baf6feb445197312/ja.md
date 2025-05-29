```
plot_basic(tt::Vector, y::Vector, ind = trues(length(tt));
           lab::String      = "",
           xlab::String     = "時間 [分]",
           ylab::String     = "",
           show_plot::Bool  = true,
           save_plot::Bool  = false,
           plot_png::String = "データ_vs_時間.png")
```

データと時間のプロット。

**引数:**

  * `tt`:        長さ`N`の時間ベクトル [s]
  * `y`:         長さ`N`のデータベクトル
  * `ind`:       （オプション）選択されたデータインデックス
  * `lab`:       （オプション）データ（凡例）ラベル
  * `xlab`:      （オプション）x軸ラベル
  * `ylab`:      （オプション）y軸ラベル
  * `show_plot`: （オプション）trueの場合、`p1`を表示
  * `save_plot`: （オプション）trueの場合、`p1`を`plot_png`として保存
  * `plot_png`:  （オプション）保存するプロットファイル名（`.png`拡張子はオプション）

**戻り値:**

  * `p1`: `y`対`tt`のプロット
