```
isosurface(x, y, z, V; kw...)
isosurface!(p, args...; kw...)
```

体積データまたは指定された暗黙の関数から等値面を抽出してプロットします。

# 使用法

```
isosurface(x, y, z, V; isovalue = 0, centroid = true, canvas = UnicodePlots.BrailleCanvas, title = "", xlabel = "", ylabel = "", zlabel = "", height = 15, width = 40, border = :solid, compact = false, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, colorbar = false, colorbar_border = :solid, colorbar_lim = (0, 1), colormap = :viridis, yflip = false, xflip = false, projection = :orthographic, elevation = 35.264389682754654, azimuth = 45.0, axes3d = true, zoom = 1.0, up = :z, zlim = (0, 0))
```

# 引数

  * **`V`** : 表面が抽出される対象の `Array` (ボリューム) または `Function` で `f(x, y, z)` として評価されます。
  * **`isovalue`** : 選択された表面の等値。
  * **`cull`** : 背面をカリング（非表示）します。
  * **`legacy`** : トポロジー強化アルゴリズムの代わりにレガシーのマーチングキューブアルゴリズムを使用します。
  * **`centroid`** : 三角形の頂点の代わりに三角形の重心を表示します。
  * **`x`** : 各点の水平方向の位置。
  * **`y`** : 各点の垂直方向の位置。
  * **`z`** : 各点の深さの位置。
  * **`title::String = ""`** : プロットの上部に表示されるテキスト。
  * **`name::String = ""`** : 右側に表示される現在の描画注釈。
  * **`xlabel::String = ""`** : プロットの `x` 軸に表示されるテキスト。
  * **`ylabel::String = ""`** : プロットの `y` 軸に表示されるテキスト。
  * **`zlabel::String = ""`** : プロットの `z` 軸（カラーバー）に表示されるテキスト。
  * **`labels::Bool = true`** : プロットラベルを表示します。
  * **`border::Symbol = :solid`** : プロットの境界ボックススタイル（`:corners`, `:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`）。
  * **`margin::Int = 3`** : プロット全体の左側にある空の文字の数。
  * **`padding::Int = 1`** : ラベルとキャンバスの間の左右のスペース。
  * **`height::Int = 15`** : キャンバスの行数、または `:auto`。
  * **`width::Int = 40`** : キャンバスの行ごとの文字数、または `:auto`。
  * **`xlim::Tuple = (0, 0)`** : `x` 軸のプロット範囲（`(0, 0)` は自動を意味します）。
  * **`ylim::Tuple = (0, 0)`** : `y` 軸のプロット範囲。
  * **`zlim::Tuple = (0, 0)`** : カラーマップスケールデータ範囲。
  * **`xflip::Bool = false`** : `x` 軸を反転するには `true` に設定します。
  * **`yflip::Bool = false`** : `y` 軸を反転するには `true` に設定します。
  * **`colorbar::Bool = false`** : カラーバーを切り替えます。
  * **`colormap::Symbol = :viridis`** : `ColorSchemes.jl` からシンボルを選択します。例： `:viridis`、または関数 `f: (z, zmin, zmax) -> Int(0-255)`、または RGB タプルのベクトルを提供します。
  * **`colorbar_lim::Tuple = (0, 1)`** : カラーバーの制限。
  * **`colorbar_border::Symbol = :solid`** : カラーバーの境界ボックススタイル（`:solid`, `:bold`, `:dashed`, `:dotted`, `:ascii`, `:none`）。
  * **`canvas::UnionAll = UnicodePlots.BrailleCanvas`** : 描画に使用されるキャンバスのタイプ。
  * **`compact::Bool = false`** : コンパクトなプロットラベル。
  * **`unicode_exponent::Bool = true`** : 指数に `Unicode` シンボルを使用します。例： `10²⸱¹` の代わりに `10^2.1`。
  * **`projection::Symbol = :orthographic`** : 3D プロットの投影（`:ortho(graphic)`, `:persp(ective)`、または `Model-View-Projection` (MVP) 行列）。
  * **`axes3d::Bool = true`** : 3D 軸を描画します（`x -> :red`, `y -> :green`, `z -> :blue`）。
  * **`elevation::Float = 35.264389682754654`** : `floor` 平面の上または下の標高角度（`-90 ≤ θ ≤ 90`）。
  * **`azimuth::Float = 45.0`** : `up` ベクトルの周りの方位角（`-180° ≤ φ ≤ 180°`）。
  * **`zoom::Float = 1.0`** : 3D のズーム係数。
  * **`up::Symbol = :z`** : 上向きベクトル（`:x`, `:y` または `:z`）、符号を変更するには `m -> -` または `p -> +` を接頭辞として付けます。例： `:mz` は `-z` 軸が上を向くことを意味します。

# 著者

  * T Bltg (github.com/t-bltg)

# 例

```julia-repl
julia> torus(x, y, z, r = .2, R = .5) = (√(x^2 + y^2) - R)^2 + z^2 - r^2
julia> isosurface(-1:.1:1, -1:.1:1, -1:.1:1, torus, elevation = 50, zoom = 2, cull = true)
    ┌────────────────────────────────────────┐ 
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⢀⢀⠠⢄⢄⠄⠄⡠⡠⠤⡀⡀⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⡀⠔⠌⠜⠀⠡⠠⠁⠡⠠⠁⠈⠄⠌⠈⠄⠌⠀⠪⠠⠤⡀⡀⠀⠀⠀⠀⠀⠀⠀⠀│ 
    │⠀⠀⠀⠀⠀⠀⡠⠔⠅⠌⠈⠄⠌⠀⡁⡀⠨⡀⠄⠠⠡⠠⡀⠥⠠⠈⠀⠡⠠⠁⠡⠱⠢⡀⠀⠀⠀⠀⠀⠀│ 
    │⠀⠀⠀⠀⢀⣜⠃⡁⠄⢊⠈⠄⡰⠐⡀⢂⡞⢈⡰⡨⡂⢆⡁⣱⠔⢁⠘⢀⠠⠁⡑⠠⢈⠘⣲⡀⠀⠀⠀⠀│ 
    │⠀⠀⠀⠀⡚⠥⠁⡀⠂⢂⠈⠄⡖⡫⠗⠋⠉⠀⠀⠀⠀⠀⠈⠉⠉⠱⢝⠱⠠⠁⡐⠐⢀⠈⢌⢧⠀⠀⠀⠀│ 
    │⠀⠀⠀⠀⡟⠤⠁⡀⠂⢂⢈⠄⢮⡇⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢸⡿⠠⡁⡐⠐⢀⠈⢤⢚⠀⠀⠀⠀│ 
    │⠀⠀⠀⠀⢽⠗⠅⡀⠂⢂⢀⠂⢂⠓⡢⡄⣀⠀⠀⠀⠀⠀⢀⡀⢀⢰⠂⡑⠐⡀⡐⠐⠀⠨⢔⡟⠀⠀⠀⠀│ 
    │⠀⠀⠀⠀⠈⠭⠄⠌⠰⠀⡀⠂⢂⠀⡐⠐⠌⠔⠑⠅⠡⠊⠢⠡⠂⢂⠀⡐⠐⣀⠐⠠⡁⡃⡑⠁⠀⠀⠀⠀│ 
    │⠀⠀⠀⠀⠀⠀⠈⠨⠅⠄⠌⠀⡆⢀⠐⠐⢀⠐⠐⠀⠄⠂⠂⡀⠂⡂⡀⠂⢂⠀⡂⢐⠔⠈⠀⠀⠀⠀⠀⠀│ 
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠢⢥⢀⡂⡃⠇⠃⡁⡡⠨⡈⡨⠈⠬⠨⠢⢈⢠⠑⠒⠈⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
    │⠀⠀⠀⢠⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠈⠋⠓⠂⠊⠒⠂⠚⠘⠚⠙⠉⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
    │⠀⠀⣀⠼⢄⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
    │⠔⠉⠀⠀⠀⠈⠑⠄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ 
    └────────────────────────────────────────┘ 
```

# 参照

`Plot`, `MVP`, `surfaceplot`, `BrailleCanvas`
