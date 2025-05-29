```
horizontal_histogram(hist; kw...)
```

# 説明

与えられた `StatsBase.Histogram` の水平ヒストグラムを描画します。

内部的には、`horizontal_histogram` は [`barplot`](@ref) の単純なラッパーであり、同じキーワード引数をサポートしています。

# 使用法

```
horizontal_histogram(hist; border = :barplot, color = :green, title = "", xlabel = "", ylabel = "", xscale = :identity, width = 40, compact = false, blend = true, xlim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, yflip = false, xflip = false, symbols = ['■'], name = "")
```

# 引数

  * **`hist`** : プロットされるべきフィッティングされた `StatsBase.Histogram`。
  * **`symbols::Array = ['■']`** : バーを描画するために使用される文字のコレクション。
  * **`title::String = ""`** : プロットの上部に表示されるテキスト。
  * **`name::String = ""`** : 右側に表示される現在の描画注釈。
  * **`xlabel::String = ""`** : プロットの `x` 軸に表示されるテキスト。
  * **`ylabel::String = ""`** : プロットの `y` 軸に表示されるテキスト。
  * **`xscale::Symbol = :identity`** : `x` 軸のスケール（`:identity`, `:ln`, `:log2`, `:log10`）、またはスケール関数（例：`x -> log10(x)`）。
  * **`yscale::Symbol = :identity`** : `y` 軸のスケール。
  * **`labels::Bool = true`** : プロットラベルを表示。
  * **`border::Symbol = :solid`** : プロットの境界ボックススタイル（`:corners`, `:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`）。
  * **`margin::Int = 3`** : プロット全体の左側にある空の文字の数。
  * **`padding::Int = 1`** : ラベルとキャンバスの間の左右のスペース。
  * **`height::Int = 15`** : キャンバスの行数、または `:auto`。
  * **`width::Int = 40`** : キャンバスの行ごとの文字数、または `:auto`。
  * **`xlim::Tuple = (0, 0)`** : `x` 軸のプロット範囲（`(0, 0)` は自動を意味します）。
  * **`ylim::Tuple = (0, 0)`** : `y` 軸のプロット範囲。
  * **`xflip::Bool = false`** : `true` に設定すると `x` 軸を反転します。
  * **`yflip::Bool = false`** : `true` に設定すると `y` 軸を反転します。
  * **`grid::Bool = true`** : 原点にグリッドラインを描画します。
  * **`compact::Bool = false`** : コンパクトなプロットラベル。
  * **`unicode_exponent::Bool = true`** : 指数に `Unicode` シンボルを使用します：例 `10²⸱¹` の代わりに `10^2.1`。
  * **`blend::Bool = true`** : 基盤となるキャンバスで色をブレンドします。
