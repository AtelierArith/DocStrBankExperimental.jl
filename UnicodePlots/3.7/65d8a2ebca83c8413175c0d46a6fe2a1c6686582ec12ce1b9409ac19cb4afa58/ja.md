```
Plot(graphics; kw...)
```

# 説明

`GraphicsArea`（または`Canvas`）オブジェクトの装飾です。タイトル、境界線、軸ラベルなどの追加情報で内部の`GraphicsArea`オブジェクトを囲むために使用されます。

# 使用法

```
Plot(graphics; title = "", xlabel = "", ylabel = "", zlabel = "", border = :solid, compact = false, margin = 3, padding = 1, labels = true)

Plot(x, y, z, canvas; title = "", xlabel = "", ylabel = "", xscale = :identity, yscale = :identity, height = 15, width = 40, border = :solid, compact = false, blend = true, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, grid = true, yflip = false, xflip = false, name = "")
```

# 引数

  * **`graphics`** : プロットが装飾する`GraphicsArea`（例：`Canvas`のサブタイプ）。
  * **`x`** : 各点の水平方向の位置。
  * **`y`** : 各点の垂直方向の位置。
  * **`z`** : 各点の深さの位置。
  * **`title::String = ""`** : プロットの上部に表示されるテキスト。
  * **`name::String = ""`** : 右側に表示される現在の描画注釈。
  * **`xlabel::String = ""`** : プロットの`x`軸に表示されるテキスト。
  * **`ylabel::String = ""`** : プロットの`y`軸に表示されるテキスト。
  * **`xscale::Symbol = :identity`** : `x`軸のスケール（`:identity`, `:ln`, `:log2`, `:log10`）、またはスケール関数（例：`x -> log10(x)`）。
  * **`yscale::Symbol = :identity`** : `y`軸のスケール。
  * **`labels::Bool = true`** : プロットラベルを表示。
  * **`border::Symbol = :solid`** : プロットの境界ボックススタイル（`:corners`, `:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`）。
  * **`margin::Int = 3`** : プロット全体の左側の空白文字数。
  * **`padding::Int = 1`** : ラベルとキャンバスの間の左右のスペース。
  * **`height::Int = 15`** : キャンバスの行数、または`:auto`。
  * **`width::Int = 40`** : キャンバスの行あたりの文字数、または`:auto`。
  * **`xlim::Tuple = (0, 0)`** : `x`軸のプロット範囲（`(0, 0)`は自動を意味します）。
  * **`ylim::Tuple = (0, 0)`** : `y`軸のプロット範囲。
  * **`xflip::Bool = false`** : `x`軸を反転するには`true`に設定。
  * **`yflip::Bool = false`** : `y`軸を反転するには`true`に設定。
  * **`canvas::UnionAll = UnicodePlots.BrailleCanvas`** : 描画に使用されるキャンバスのタイプ。
  * **`grid::Bool = true`** : 原点にグリッドラインを描画。
  * **`compact::Bool = false`** : コンパクトなプロットラベル。
  * **`unicode_exponent::Bool = true`** : 指数に`Unicode`シンボルを使用：例：`10²⸱¹`の代わりに`10^2.1`。
  * **`blend::Bool = true`** : 基盤となるキャンバスで色をブレンド。

# メソッド

  * `title!(plot::Plot, title::String)`
  * `xlabel!(plot::Plot, xlabel::String)`
  * `ylabel!(plot::Plot, xlabel::String)`
  * `zlabel!(plot::Plot, zlabel::String)`
  * `label!(plot::Plot, where::Symbol, value::String)`
  * `label!(plot::Plot, where::Symbol, row::Integer, value::String)`

著者

  * Christof Stocker (github.com/Evizero)

# 参照

[`scatterplot`](@ref), [`lineplot`](@ref), [`BarplotGraphics`](@ref), [`BrailleCanvas`](@ref), [`BlockCanvas`](@ref), [`AsciiCanvas`](@ref)
