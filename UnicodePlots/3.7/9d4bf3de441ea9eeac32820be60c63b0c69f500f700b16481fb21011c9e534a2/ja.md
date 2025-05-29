```
scatterplot(; kw...)
scatterplot(y; kw...)
scatterplot(x, y; kw...)
scatterplot!(p, args...; kw...)
```

# 説明

与えられた点を新しいキャンバスに描画します。

最初の（オプションの）ベクトル `x` は、すべての点の水平方向の位置を含む必要があります。次のベクトル `y` は、それぞれの対応する垂直方向の位置を含む必要があります。これは、2つのベクトルが同じ長さと順序でなければならないことを意味します。

# 使用法

```
scatterplot([x], y; canvas = UnicodePlots.BrailleCanvas, title = "", xlabel = "", ylabel = "", xscale = :identity, yscale = :identity, height = 15, width = 40, border = :solid, compact = false, blend = true, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, grid = true, yflip = false, xflip = false, name = "")
```

# 引数

  * **`marker`** : (:circle, :rect, :diamond, :hexagon, :cross, :xcross, :utriangle, :dtriangle, :rtriangle, :ltriangle, :pentagon, :star4, :star5, :star6, :star8, :vline, :hline, :+, :x) からマーカーを選択するか、`Char`、単位長の `String`、またはこれらの `Vector`。
  * **`color::Symbol = :auto`** : 色の `Vector` またはスカラー - （`:green`, `:blue`, `:red`, `:yellow`, `:cyan`, `:magenta`, `:white`, `:normal`, `:auto`）から選択するか、`[0-255]` の整数を使用するか、`RGB` コンポーネントとして `3` つの整数を提供します。
  * **`x`** : 各点の水平方向の位置。
  * **`y`** : 各点の垂直方向の位置。
  * **`title::String = ""`** : プロットの上部に表示されるテキスト。
  * **`name::String = ""`** : 右側に表示される現在の描画注釈。
  * **`xlabel::String = ""`** : プロットの `x` 軸に表示されるテキスト。
  * **`ylabel::String = ""`** : プロットの `y` 軸に表示されるテキスト。
  * **`xscale::Symbol = :identity`** : `x` 軸のスケール（`:identity`, `:ln`, `:log2`, `:log10`）、またはスケール関数（例：`x -> log10(x)`）。
  * **`yscale::Symbol = :identity`** : `y` 軸のスケール。
  * **`labels::Bool = true`** : プロットラベルを表示します。
  * **`border::Symbol = :solid`** : プロットの境界ボックススタイル（`:corners`, `:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`）。
  * **`margin::Int = 3`** : プロット全体の左側の空白文字の数。
  * **`padding::Int = 1`** : ラベルとキャンバスの間の左右のスペース。
  * **`height::Int = 15`** : キャンバスの行数、または `:auto`。
  * **`width::Int = 40`** : キャンバスの行ごとの文字数、または `:auto`。
  * **`xlim::Tuple = (0, 0)`** : `x` 軸のプロット範囲（`(0, 0)` は自動を意味します）。
  * **`ylim::Tuple = (0, 0)`** : `y` 軸のプロット範囲。
  * **`xflip::Bool = false`** : `x` 軸を反転させるには `true` に設定します。
  * **`yflip::Bool = false`** : `y` 軸を反転させるには `true` に設定します。
  * **`canvas::UnionAll = UnicodePlots.BrailleCanvas`** : 描画に使用されるキャンバスの種類。
  * **`grid::Bool = true`** : 原点にグリッドラインを描画します。
  * **`compact::Bool = false`** : コンパクトなプロットラベル。
  * **`unicode_exponent::Bool = true`** : 指数に `Unicode` シンボルを使用します：例 `10²⸱¹` の代わりに `10^2.1`。
  * **`blend::Bool = true`** : 基盤となるキャンバスで色をブレンドします。

著者

  * Christof Stocker (github.com/Evizero)

# 例

```julia-repl
julia> scatterplot(randn(50), randn(50), title = "My Scatterplot")
      ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀My Scatterplot⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀ 
      ┌────────────────────────────────────────┐ 
    3 │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
      │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
      │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠄⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠀⠀⠠⠀⠀⠀│ 
      │⠀⠀⠀⠀⠀⠀⠀⠀⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠠⠀⠀⠂⡀⠀⠀⠀⠀⠀⠄⠀⠀⠀⠀⠀⠀│ 
      │⠈⠀⠀⠀⠀⠠⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠌⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
      │⠀⠀⠠⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠄⠀⠀⠀⠀⠀⠀⡇⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠠⠀⡀⠀⠀⠀⠀│ 
      │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡀⠀⠀⠀⠀⠀⠀⠀⠀⡀⡏⠀⠉⠀⠀⠂⠀⠠⠀⠄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
      │⠤⠤⠤⠤⠤⠤⠤⠴⠤⢤⠤⠤⠤⠤⠤⠤⠤⠬⠤⢤⠤⡧⠤⢤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤│ 
      │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠠⠀⠀⠀⠀⠀⠂⠀⠀⡇⠀⠀⠀⠂⠠⡀⠀⡀⠀⠀⠀⡀⠀⠀⠀⠀⠀⠀⠀│ 
      │⠀⠀⠀⠀⠀⠀⠄⠀⠀⠀⠀⠀⠀⠄⠀⠀⠀⠈⠀⠀⡇⠀⠀⠀⠀⠈⠀⠀⠀⠁⠀⠀⠀⠀⠐⠀⠀⠀⠀⠀│ 
      │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠐⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
      │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡀⠀⠀⠀⡇⠀⠠⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠐⠀⠀⠀⠀⠀│ 
      │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
      │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
   -3 │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠐⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
      └────────────────────────────────────────┘ 
      ⠀-2⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀2⠀ 
```

# 参照

[`Plot`](@ref), [`lineplot`](@ref), [`stairs`](@ref), [`BrailleCanvas`](@ref), [`BlockCanvas`](@ref), [`AsciiCanvas`](@ref), [`DotCanvas`](@ref)
