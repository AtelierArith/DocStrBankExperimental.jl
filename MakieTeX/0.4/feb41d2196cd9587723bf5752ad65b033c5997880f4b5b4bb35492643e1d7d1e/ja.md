```
teximg(tex; position, ...)
teximg!(ax_or_scene, tex; position, ...)
```

このレシピは、レンダリングされた `TeX` をあなたの図またはシーンにプロットします。

提供できる入力のタイプは3つあります：

  * 任意の `String`、これは図の全体的なテーマを考慮して LaTeX にレンダリングされます。
  * [`TeXDocument`](@ref) オブジェクト、これは LaTeX に直接レンダリングされ、ユーザーによってカスタマイズ可能です。
  * [`CachedTeX`](@ref) オブジェクト、これは事前にレンダリングされた LaTeX ドキュメントです。

`tex` はこれらのオブジェクトのいずれか1つ、またはそれらの配列である可能性があります。

## 属性

`MakieCore.Plot{MakieTeX.teximg}` の利用可能な属性とそのデフォルトは次のとおりです：

```
  align            (:center, :center)
  clip_planes      MakieCore.Automatic()
  depth_shift      0.0f0
  inspectable      true
  inspector_clear  MakieCore.Automatic()
  inspector_hover  MakieCore.Automatic()
  inspector_label  MakieCore.Automatic()
  markerspace      :pixel
  overdraw         false
  position         GeometryBasics.Point{2, Float32}[[0.0, 0.0]]
  render_density   2
  rotation         Float32[0.0]
  scale            1.0
  space            :data
  ssao             false
  transparency     false
  visible          true
```
