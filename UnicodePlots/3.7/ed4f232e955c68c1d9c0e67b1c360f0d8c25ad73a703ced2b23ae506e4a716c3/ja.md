```
densityplot(x, y; kw...)
densityplot!(p, args...; kw...)
```

# 説明

与えられた点の密度プロットを描画します。

最初のベクトル `x` はすべての点の水平方向の位置を含む必要があります。2番目のベクトル `y` はそれぞれの対応する垂直方向の位置を含む必要があります。したがって、2つのベクトルは同じ長さと順序でなければなりません。密度カウントを変換するために任意の `dscale`（`Function` または `Symbol`）を渡すことができます（例：ピークの減衰）。

# 使用法

```
densityplot(x, y; dscale = :identity, title = "", xlabel = "", ylabel = "", xscale = :identity, yscale = :identity, height = 15, width = 40, border = :solid, compact = false, blend = true, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, yflip = false, xflip = false, name = "")
```

# 引数

  * **`dscale`** : 密度スケール関数。
  * **`x`** : 各点の水平方向の位置。
  * **`y`** : 各点の垂直方向の位置。
  * **`title::String = ""`** : プロットの上部に表示されるテキスト。
  * **`name::String = ""`** : 右側に表示される現在の描画注釈。
  * **`xlabel::String = ""`** : プロットの `x` 軸に表示されるテキスト。
  * **`ylabel::String = ""`** : プロットの `y` 軸に表示されるテキスト。
  * **`xscale::Symbol = :identity`** : `x` 軸のスケール（`:identity`, `:ln`, `:log2`, `:log10`）、またはスケール関数（例：`x -> log10(x)`）。
  * **`yscale::Symbol = :identity`** : `y` 軸のスケール。
  * **`labels::Bool = true`** : プロットラベルを表示する。
  * **`border::Symbol = :solid`** : プロットの境界ボックススタイル（`:corners`, `:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`）。
  * **`margin::Int = 3`** : プロット全体の左側の空白文字数。
  * **`padding::Int = 1`** : ラベルとキャンバスの間の左右のスペース。
  * **`height::Int = 15`** : キャンバスの行数、または `:auto`。
  * **`width::Int = 40`** : キャンバスの行あたりの文字数、または `:auto`。
  * **`xlim::Tuple = (0, 0)`** : `x` 軸のプロット範囲（`(0, 0)` は自動を意味します）。
  * **`ylim::Tuple = (0, 0)`** : `y` 軸のプロット範囲。
  * **`xflip::Bool = false`** : `x` 軸を反転させるには `true` に設定します。
  * **`yflip::Bool = false`** : `y` 軸を反転させるには `true` に設定します。
  * **`compact::Bool = false`** : コンパクトなプロットラベル。
  * **`unicode_exponent::Bool = true`** : 指数に `Unicode` シンボルを使用します：例：`10²⸱¹` の代わりに `10^2.1`。
  * **`blend::Bool = true`** : 基盤となるキャンバスで色をブレンドします。

# 著者

  * Christof Stocker (github.com/Evizero)

# 例

```julia-repl
julia> densityplot(randn(1_000), randn(1_000); title = "Density Plot")
                     Density Plot                
      ┌────────────────────────────────────────┐ 
    4 │                                        │ 
      │                                        │ 
      │                                        │ 
      │                                        │ 
      │          ░        ░░  ░                │ 
      │           ░ ░░░░░░▓▒▒▒░░░░░            │ 
      │            ░▒▒▓▒░▒▒▓▓▓▒▒░░░░           │ 
      │         ░░  ░░▓▓░▓▒█▓▒░░▒░░░           │ 
      │            ░░░▒▒▒░▒▓▒▒▒░░░░░           │ 
      │          ░  ░░░░░▓░░░░░░░ ░            │ 
      │                 ░░░░░ ░  ░             │ 
      │                                        │ 
      │                                        │ 
      │                                        │ 
   -4 │                                        │ 
      └────────────────────────────────────────┘ 
       -4                                     4  
```

# 参照

[`Plot`](@ref), [`scatterplot`](@ref), [`DensityCanvas`](@ref)
