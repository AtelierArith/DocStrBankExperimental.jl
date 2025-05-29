```
heatmap(A; kw...)
```

# 説明

与えられた点のヒートマップを描画します。行列 `A` をヒートマップの値として使用し、行列の列および行のインデックスをそれぞれ `x` および `y` 座標として使用します。

# 使用法

```
heatmap(A::AbstractMatrix; height = 0, width = 0, yfact = nothing, xfact = nothing, array = false, title = "", xlabel = "", ylabel = "", zlabel = "", xscale = :identity, yscale = :identity, border = :solid, compact = false, blend = true, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, colorbar = false, colorbar_border = :solid, colorbar_lim = (0, 1), colormap = :viridis, grid = true, yflip = false, xflip = false, name = "", zlim = (0, 0), fix_ar = false)
```

# 引数

  * **`A`** : 入力行列（色の値）。
  * **`yfact`** : `y` 座標ラベルのスケール（デフォルトは 0 - すなわち、`A` の各行が 1 ユニットにマッピングされ、`y` 原点は 1 から始まります）。他の値に設定すると、`y` 原点は 0 から始まります。
  * **`xfact`** : `x` 座標のスケール（デフォルトは 0 - すなわち、`A` の各列が 1 ユニットにマッピングされ、`x` 原点は 1 から始まります）。他の値に設定すると、`x` 原点は 0 から始まります。
  * **`yoffset`** : `y` 座標のプロットオフセット（スケーリング後）。
  * **`xoffset`** : `x` 座標のプロットオフセット（スケーリング後）。
  * **`array`** : 配列表示の慣習を使用（プロットの北西隅に原点があるため、通常のプロットに対して `y` を反転させます）。
  * **`title::String = ""`** : プロットの上部に表示されるテキスト。
  * **`name::String = ""`** : 右側に表示される現在の描画注釈。
  * **`xlabel::String = ""`** : プロットの `x` 軸に表示されるテキスト。
  * **`ylabel::String = ""`** : プロットの `y` 軸に表示されるテキスト。
  * **`zlabel::String = ""`** : プロットの `z` 軸（カラーバー）に表示されるテキスト。
  * **`xscale::Symbol = :identity`** : `x` 軸のスケール（`:identity`, `:ln`, `:log2`, `:log10`）、またはスケール関数 e.g. `x -> log10(x)`。
  * **`yscale::Symbol = :identity`** : `y` 軸のスケール。
  * **`labels::Bool = true`** : プロットラベルを表示。
  * **`border::Symbol = :solid`** : プロットの境界ボックススタイル（`:corners`, `:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`）。
  * **`margin::Int = 3`** : プロット全体の左側の空白文字数。
  * **`padding::Int = 1`** : ラベルとキャンバスの間の左右のスペース。
  * **`height::Int = 15`** : キャンバスの行数、または `:auto`。
  * **`width::Int = 40`** : キャンバスの行あたりの文字数、または `:auto`。
  * **`xlim::Tuple = (0, 0)`** : `x` 軸のプロット範囲（`(0, 0)` は自動を意味します）。
  * **`ylim::Tuple = (0, 0)`** : `y` 軸のプロット範囲。
  * **`zlim::Tuple = (0, 0)`** : カラーマップスケールデータ範囲。
  * **`xflip::Bool = false`** : `true` に設定すると `x` 軸を反転します。
  * **`yflip::Bool = false`** : `true` に設定すると `y` 軸を反転します。
  * **`colorbar::Bool = false`** : カラーバーを切り替えます。
  * **`colormap::Symbol = :viridis`** : `ColorSchemes.jl` からシンボルを選択 e.g. `:viridis`、または関数 `f: (z, zmin, zmax) -> Int(0-255)`、または RGB タプルのベクトルを提供します。
  * **`colorbar_lim::Tuple = (0, 1)`** : カラーバーの制限。
  * **`colorbar_border::Symbol = :solid`** : カラーバーの境界ボックススタイル（`:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`）。
  * **`grid::Bool = true`** : 原点にグリッドラインを描画します。
  * **`compact::Bool = false`** : コンパクトなプロットラベル。
  * **`unicode_exponent::Bool = true`** : 指数に `Unicode` シンボルを使用：e.g. `10²⸱¹` の代わりに `10^2.1`。
  * **`blend::Bool = true`** : 基盤キャンバス上で色をブレンドします。
  * **`fix_ar::Bool = false`** : ターミナルのアスペクト比を固定します（実験的）。

# 著者

  * Rowan Katekar (github.com/rjkat)

# 例

```julia-repl
julia> heatmap(repeat(collect(0:10)', outer=(11, 1)), zlabel="z")
      ┌───────────┐  10   
   11 │▄▄▄▄▄▄▄▄▄▄▄│ ┌──┐  
      │▄▄▄▄▄▄▄▄▄▄▄│ │▄▄│  
      │▄▄▄▄▄▄▄▄▄▄▄│ │▄▄│  
      │▄▄▄▄▄▄▄▄▄▄▄│ │▄▄│ z
      │▄▄▄▄▄▄▄▄▄▄▄│ │▄▄│  
    1 │▄▄▄▄▄▄▄▄▄▄▄│ └──┘  
      └───────────┘  0    
       1        11        
```

# 参照

`Plot`, `HeatmapCanvas`
