```
tooltip(position, string)
tooltip(x, y, string)
```

指定された `string` を表示する `position` を指すツールチップを作成します。

## 属性

### 一般

  * `visible::Bool = true` は、プロットが描画されるかどうかを設定します。
  * `overdraw::Bool = false` は、プロットが他のプロットの上に描画されるかどうかを設定します。これは特にGLバックエンドで深度チェックを無視することを意味します。
  * `transparency::Bool = false` は、プロットが透明性をどのように扱うかを調整します。GLMakieでは `transparency = true` は順序独立透明性を使用する結果になります。
  * `inspectable::Bool = true` は、このプロットが `DataInspector` に表示されるべきかどうかを設定します。
  * `depth_shift::Float32 = 0f0` は、すべての他の変換の後にプロットの深度値を調整します。すなわち、クリップ空間で、`0 <= depth <= 1` の範囲です。これはGLMakieおよびWGLMakieにのみ適用され、レンダー順序を調整するために使用できます（調整可能なオーバードローのように）。
  * `space::Symbol = :data` は、マーカーの位置の変換空間を設定します。可能な入力については `Makie.spaces()` を参照してください。

### ツールチップ特有

  * `offset = 10` は、指定された `position` とその位置を指す三角形の先端との間のオフセットを設定します。
  * `placement = :above` は、ツールチップが `position` に対してどこに配置されるべきかを設定します。`:above`、`:below`、`:left`、`:right` のいずれかです。
  * `align = 0.5` は、ツールチップの `position` に対する整列を設定します。`align = 0.5` の場合、ツールチップは `position` の上/下/左/右に中央に配置されます。
  * `backgroundcolor = :white` は、ツールチップの背景色を設定します。
  * `triangle_size = 10` は、`position` を指す三角形のサイズを設定します。
  * `outline_color = :black` は、ツールチップのアウトラインの色を設定します。
  * `outline_linewidth = 2f0` は、ツールチップのアウトラインの線幅を設定します。
  * `outline_linestyle = nothing` は、ツールチップのアウトラインの線スタイルを設定します。
  * `textpadding = (4, 4, 4, 4)` は、ツールチップ内のテキストの周りのパディングを設定します。これは `(左, 右, 下, 上)` のオフセットとして与えられます。
  * `textcolor = theme(scene, :textcolor)` は、テキストの色を設定します。
  * `fontsize = 16` は、テキストのサイズを設定します。
  * `font = theme(scene, :font)` は、フォントを設定します。
  * `strokewidth = 0`: 正の値に設定すると、テキストにアウトラインを付けます。
  * `strokecolor = :white` は、テキストのアウトラインの色を設定します。
  * `justification = :left` は、テキストがそのバウンディングボックス内で `:left`、`:center` または `:right` に整列されるかどうかを設定します。
