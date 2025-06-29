```
render_storyboard(anim::Animation, [idxs]; options...)
```

[`Animation`](@ref)をストーリーボード内の一連の（ビットマップ）画像としてレンダリングします。各フレームがサブプロットである`Figure`を返します。

レンダリングするフレームは、インデックスのベクトルである`idxs`によって指定できます。`idxs`が指定されていない場合、すべてのフレームがレンダリングされます。

# オプション

  * `n_rows = 1`: ストーリーボードの行数。
  * `n_cols = nothing`: ストーリーボードの列数（デフォルト：フレームの数）。
  * `figscale = 1`: すべてのフレームをそのフル解像度で収めるために必要なピクセル数に対する図のサイズのスケール。
  * `titles`: フレームタイトルのリストまたは辞書。
  * `subtitles`: フレームサブタイトルのリストまたは辞書。
  * `xlabels`: 各フレームのx軸ラベルのリストまたは辞書。
  * `ylabels`: 各フレームのy軸ラベルのリストまたは辞書。

タイトルやラベルのスタイリングを制御するオプション（例：`titlesize`）もキーワード引数として指定できます。詳細は`Axis`を参照してください。
