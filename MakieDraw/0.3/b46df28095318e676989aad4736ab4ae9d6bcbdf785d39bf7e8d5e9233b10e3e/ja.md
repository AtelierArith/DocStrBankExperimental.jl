```
PaintCanvas <: AbstractCanvas

PaintCanvas(; kw...)
PaintCanvas(f, data; kw...)
```

行列の実数または色を描画するためのキャンバスです。

# 引数

  * `data`: `Makie.image!`でプロットする`AbstractMatrix`、またはあなたの関数`f`
  * `f`: `image!`や`heatmap!`のような関数で、`f(axis, dimsions..., data)`を`axis`にプロットします。

# キーワード

  * `dimension`: データの次元ティック。デフォルトでは`axes(data)`。
  * `drawing`: 描画が行われているかを追跡するためのObservable{Bool}(false)。
  * `drawbutton`: 描画中に現在クリックされているマウスボタン、例: Mouse.left。
  * `active`: キャンバスがアクティブかどうかを設定するためのObservable{Bool}(true)。
  * `name`: キャンバスの名前のための`Symbol`。[`CanvasSelect`](@ref)に表示されます。
  * `figure`: プロットするためのフィギュア。
  * `axis`: プロットするための軸。
  * `fill_left`: 左クリック描画のためのObservable値。
  * `fill_right`: 右クリック描画のためのObservable値。
  * `fill_middle`: 中クリック描画のためのObservable値。

# マウスとキーコマンド

  * 左クリック/ドラッグ: `fill_left`の値で描画
  * 右クリック/ドラッグ: `fill_right`の値で描画
  * 中クリック/ドラッグ: `fill_middle`の値で描画
