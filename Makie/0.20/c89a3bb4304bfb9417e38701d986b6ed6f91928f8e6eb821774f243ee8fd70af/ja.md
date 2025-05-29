```
DataInspector(figure_axis_or_scene = current_figure(); kwargs...)
```

プロットにマウスをホバーすると、関連情報をツールチップで表示するデータインスペクタを作成します。

この機能は、`plot.inspectable[] = false`を設定することで、プロットごとに無効にすることができます。表示されるテキストは、`plot.inspector_label`を関数`(plot, index, position) -> "my_label"`に設定することで調整できます。詳細についてはMakieのドキュメントを参照してください。

### キーワード引数:

  * `range = 10`: プロットの要素を選択するためのスナッピング範囲を制御します。
  * `priority = 100`: マウスの動きやスクロールイベントでツールチップを作成する優先度。
  * `enabled = true`: falseに設定するとプロットのインスペクションを無効にします。`enable!(inspector)`および`disable!(inspector)`で調整することもできます。
  * `indicator_color = :red`: 選択インジケーターの色。
  * `indicator_linewidth = 2`: 選択インジケーターの線の太さ。
  * `indicator_linestyle = nothing`: 選択インジケーターの線のスタイル。
  * `enable_indicators = true)`: インジケーターを有効または無効にします。
  * `depth = 9e3`: ツールチップの深さの値。この値は高く設定する必要があり、ツールチップが常に前面に表示されるようにします。
  * `apply_tooltip_offset = true`: マーカーサイズなどに基づいてツールチップのオフセットを有効または無効にします。
  * および`Tooltip`からのすべての属性。
