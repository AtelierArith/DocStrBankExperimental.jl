```
stairs(x, y; kw...)
stairs!(p, args...; kw...)
```

# 説明

新しいキャンバスに階段プロットを描画します。

最初の（オプションの）ベクトル `x` は、すべての点の水平方向の位置を含む必要があります。2番目のベクトル `y` は、それに対応する垂直方向の位置を含む必要があります。これは、2つのベクトルが同じ長さと順序である必要があることを意味します。

# 使用法

```
stairs(x, y; style = :post, canvas = UnicodePlots.BrailleCanvas, title = "", xlabel = "", ylabel = "", xscale = :identity, yscale = :identity, height = 15, width = 40, border = :solid, compact = false, blend = true, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, grid = true, yflip = false, xflip = false, name = "")
```

# 引数

  * **`style`** : 階段の遷移が行われる場所を指定します（`:pre` または `:post` のいずれか）。
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
  * **`margin::Int = 3`** : プロット全体の左側にある空の文字の数。
  * **`padding::Int = 1`** : ラベルとキャンバスの間の左右のスペース。
  * **`height::Int = 15`** : キャンバスの行数、または `:auto`。
  * **`width::Int = 40`** : キャンバスの行ごとの文字数、または `:auto`。
  * **`xlim::Tuple = (0, 0)`** : `x` 軸のプロット範囲（`(0, 0)` は自動を意味します）。
  * **`ylim::Tuple = (0, 0)`** : `y` 軸のプロット範囲。
  * **`xflip::Bool = false`** : `true` に設定すると `x` 軸を反転します。
  * **`yflip::Bool = false`** : `true` に設定すると `y` 軸を反転します。
  * **`canvas::UnionAll = UnicodePlots.BrailleCanvas`** : 描画に使用されるキャンバスのタイプ。
  * **`grid::Bool = true`** : 原点にグリッドラインを描画します。
  * **`compact::Bool = false`** : コンパクトなプロットラベル。
  * **`unicode_exponent::Bool = true`** : 指数に `Unicode` シンボルを使用します：例 `10²⸱¹` の代わりに `10^2.1`。
  * **`blend::Bool = true`** : 基盤となるキャンバスで色をブレンドします。

# 著者

  * Christof Stocker (github.com/Evizero)
  * Dominique (github.com/dpo)

# 例

```julia-repl
julia> stairs([1, 2, 4, 7, 8], [1, 3, 4, 2, 7], style = :post, title = "My Staircase Plot")
     ⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀My Staircase Plot⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀ 
     ┌────────────────────────────────────────┐ 
   7 │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⠤⡄⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⢸⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡇⠀⠀⠀⠀⢸│ 
     │⠀⠀⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠧⠤⠤⠤⠤⠼│ 
     │⠀⠀⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
   1 │⣀⣀⣀⣀⣀⣸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
     └────────────────────────────────────────┘ 
     ⠀1⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀8⠀ 
```

# 参照

[`Plot`](@ref), [`scatterplot`](@ref), [`lineplot`](@ref), [`BrailleCanvas`](@ref), [`BlockCanvas`](@ref), [`AsciiCanvas`](@ref), [`DotCanvas`](@ref)
