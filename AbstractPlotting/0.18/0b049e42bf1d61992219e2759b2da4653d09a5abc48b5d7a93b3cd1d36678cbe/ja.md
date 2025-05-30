```
DataInspector(figure; kwargs...)
```

プロットにマウスをホバーすると、関連情報をツールチップで表示するデータインスペクターを作成します。プロットを除外したい場合は、`plot.inspectable[] = false`を設定できます。

### キーワード引数:

  * `range = 10`: プロットの要素を選択するためのスナッピング範囲を制御します。
  * `enabled = true`: falseに設定するとプロットのインスペクションが無効になります。`enable!(inspector)`および`disable!(inspector)`で調整することもできます。
  * `text_padding = Vec4f0(5, 5, 3, 3)`: ツールチップテキストの周りに描画されるボックスのパディング。(左, 右, 下, 上)
  * `text_align = (:left, :bottom)`: ツールチップ内のテキストの整列。これはカーソルに対するツールチップの整列には影響しません。
  * `textcolor = :black`: ツールチップテキストの色。
  * `textsize = 20`: ツールチップテキストのサイズ。
  * `font = "Dejavu Sans"`: ツールチップのフォント。
  * `background_color = :white`: ツールチップの背景色。
  * `outline_color = :grey`: ツールチップのアウトラインの色。
  * `outline_linestyle = nothing`: ツールチップのアウトラインの線スタイル。
  * `outline_linewidth = 2`: ツールチップのアウトラインの線幅。
  * `indicator_color = :red`: 選択インジケーターの色。
  * `indicator_linewidth = 2`: 選択インジケーターの線幅。
  * `indicator_linestyle = nothing`: 選択インジケーターの線スタイル。
  * `tooltip_align = (:center, :top)`: カーソルまたは現在の選択に対するツールチップのデフォルト位置。実際の整列はツールチップを表示範囲内に保つために調整される場合があります。
  * `tooltip_offset = Vec2f0(20)`: インジケーターからツールチップまでのオフセット。
  * `depth = 9e3`: ツールチップの深さ値。ツールチップが常に前面に表示されるように高く設定する必要があります。
  * `priority = 100`: マウスの動きやスクロールイベントでツールチップを作成する優先度。
