```
surfaceplot(x, y, A; kw...)
surfaceplot!(p, args...; kw...)
```

新しいキャンバスに3Dサーフェスプロットを描画します（`NaN`を使用して値をマスキングすることがサポートされています）。スライスをプロットするには、定数の高さにマッピングされる無名関数を渡すことができます：`zscale = z -> a_constant`。デフォルトでは、`zscale = :aspect`は高さ（`z`軸）を`x`または`y`軸に正規化します。3Dデカルトフレームの`x`、`y`、`z`軸は、それぞれ`:red`、`:green`、`:blue`の色にマッピングされます。

# 使用法

```
surfaceplot(x, y, A; lines = false, canvas = UnicodePlots.BrailleCanvas, title = "", xlabel = "", ylabel = "", zlabel = "", height = 15, width = 40, border = :solid, compact = false, xlim = (0, 0), ylim = (0, 0), margin = 3, padding = 1, labels = true, unicode_exponent = true, colorbar = false, colorbar_border = :solid, colorbar_lim = (0, 1), colormap = :viridis, yflip = false, xflip = false, projection = :orthographic, elevation = 35.264389682754654, azimuth = 45.0, axes3d = true, zoom = 1.0, up = :z, name = "", zlim = (0, 0))
```

# 引数

  * **`A`** : サーフェスの高さの`Matrix`、または`f(x, y)`として評価される`Function`。
  * **`lines`** : `scatterplot`の代わりに`lineplot`を使用（通常の増加データ用）。
  * **`zscale::Symbol = :aspect`** : 高さをスケール（`:identity`、`:aspect`、(min, max)のタプル、または任意のスケール関数）。
  * **`x`** : 各点の水平方向の位置。
  * **`y`** : 各点の垂直方向の位置。
  * **`title::String = ""`** : プロットの上部に表示されるテキスト。
  * **`xlabel::String = ""`** : プロットの`x`軸に表示されるテキスト。
  * **`ylabel::String = ""`** : プロットの`y`軸に表示されるテキスト。
  * **`zlabel::String = ""`** : プロットの`z`軸（カラーバー）に表示されるテキスト。
  * **`labels::Bool = true`** : プロットラベルを表示。
  * **`border::Symbol = :solid`** : プロットのバウンディングボックススタイル（`:corners`、`:solid`、`:bold`、`:dashed`、`:dotted`、`:ascii`、`:none`）。
  * **`margin::Int = 3`** : プロット全体の左側の空白文字数。
  * **`padding::Int = 1`** : ラベルとキャンバスの間の左右のスペース。
  * **`height::Int = 15`** : キャンバスの行数、または`:auto`。
  * **`width::Int = 40`** : キャンバスの行ごとの文字数、または`:auto`。
  * **`xlim::Tuple = (0, 0)`** : `x`軸のプロット範囲（`(0, 0)`は自動を意味します）。
  * **`ylim::Tuple = (0, 0)`** : `y`軸のプロット範囲。
  * **`zlim::Tuple = (0, 0)`** : カラーマップスケールデータ範囲。
  * **`xflip::Bool = false`** : `x`軸を反転するには`true`に設定。
  * **`yflip::Bool = false`** : `y`軸を反転するには`true`に設定。
  * **`colorbar::Bool = false`** : カラーバーを切り替え。
  * **`colormap::Symbol = :viridis`** : `ColorSchemes.jl`からシンボルを選択（例：`:viridis`）、または関数`f: (z, zmin, zmax) -> Int(0-255)`、またはRGBタプルのベクトルを提供。
  * **`colorbar_lim::Tuple = (0, 1)`** : カラーバーの制限。
  * **`colorbar_border::Symbol = :solid`** : カラーバーのバウンディングボックススタイル（`:solid`、`:bold`、`:dashed`、`:dotted`、`:ascii`、`:none`）。
  * **`canvas::UnionAll = UnicodePlots.BrailleCanvas`** : 描画に使用されるキャンバスのタイプ。
  * **`compact::Bool = false`** : コンパクトなプロットラベル。
  * **`unicode_exponent::Bool = true`** : 指数に`Unicode`シンボルを使用：例：`10²⸱¹`の代わりに`10^2.1`。
  * **`projection::Symbol = :orthographic`** : 3Dプロットの投影（`:ortho(graphic)`、`:persp(ective)`、または`Model-View-Projection`（MVP）行列）。
  * **`axes3d::Bool = true`** : 3D軸を描画（`x -> :red`、`y -> :green`、`z -> :blue`）。
  * **`elevation::Float = 35.264389682754654`** : `floor`平面の上または下の標高角度（`-90 ≤ θ ≤ 90`）。
  * **`azimuth::Float = 45.0`** : `up`ベクトルの周りの方位角（`-180° ≤ φ ≤ 180°`）。
  * **`zoom::Float = 1.0`** : 3Dのズーム係数。
  * **`up::Symbol = :z`** : 上向きベクトル（`:x`、`:y`または`:z`）、符号を変更するには`m -> -`または`p -> +`を接頭辞として付けて、例：`:mz`は`-z`軸が上を指す。

# 著者

  * T Bltg (github.com/t-bltg)

# 例

```julia-repl
julia> sombrero(x, y) = 15sinc(√(x^2 + y^2) / π)
julia> surfaceplot(-8:.5:8, -8:.5:8, sombrero)
    ┌────────────────────────────────────────┐  15 
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ ┌──┐
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡰⡃⢝⢆⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⠭⠂⠒⠭⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⣀⣠⣤⣴⣥⡅⣭⣬⣦⣤⣄⣀⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⠀⠀⣀⣤⣖⡻⠝⡪⢒⢵⣥⡫⠇⠼⢝⣬⡮⡒⢕⠫⢟⣲⣤⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⠀⠀⣠⣾⣿⢗⣒⣊⡩⠔⢁⢎⣐⡱⡁⢏⢎⣂⡱⡈⠢⢍⣑⣒⡺⣿⣷⣄⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠀⠀⣠⣾⡿⠿⣿⣿⣕⣒⣒⣊⣽⣯⡾⠵⠅⠮⠮⢷⣽⣯⣑⣒⣒⣪⣿⣿⠿⢿⣷⣄⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⠐⠻⠿⠛⠛⠛⠛⠽⢿⣶⣶⡾⠓⠉⠢⠈⡀⢀⠁⠔⠉⠚⢷⣶⣶⡿⠯⠛⠛⠛⠛⠿⠟⠂⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⢀⠀⠀⠀⠀⠀⠀⠀⠀⠘⠿⣯⣯⣓⢶⣷⡆⣶⣾⡶⣚⣽⣽⠿⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⠀⠀⢸⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠻⡳⡻⡃⢟⢟⢞⠟⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠀⢀⡠⠜⠤⣀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⠪⠆⡵⠕⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ │▄▄│
    │⠊⠁⠀⠀⠀⠀⠉⠂⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│ └──┘
    └────────────────────────────────────────┘ -3  
```

# 参照

`Plot`、`MVP`、`lineplot`、`scatterplot`、`BrailleCanvas`
