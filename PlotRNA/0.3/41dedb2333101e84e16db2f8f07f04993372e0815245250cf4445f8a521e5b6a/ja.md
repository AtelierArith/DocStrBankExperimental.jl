```
plot_structure(structure; [sequence, savepath, more plot opts...]) -> Luxor.Drawing
```

`structure`によって与えられたRNA二次構造をプロットし、オプションで`sequence`を指定します。`savepath`が空でない場合、画像はそこに書き込まれます。

プロットオプション:

  * `layout_type=:simple` グラフレイアウトアルゴリズム、`:simple`、`:naview`、`:circular`、`:turtle`、`:puzzler`のいずれか
  * `base_colors=Float64[]` `base_colorscheme`から選択するベースカラー、0.0から1.0の値のベクトル
  * `base_colorscheme::ColorScheme=colorschemes[:flag_id]`
