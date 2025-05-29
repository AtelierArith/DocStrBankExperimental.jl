```julia
available_kwargs()

```

このパッケージのすべてのメソッドに対する利用可能なキーワード引数。

  * `show`: プロットをすぐに表示します。デフォルト: `false`
  * `reveal`: プロットをすぐに表示します（:showと同じ）。デフォルト: `false`
  * `clear`: 新しいコンテンツを追加する前にプロットをクリアします。デフォルト: `true`
  * `layout`: ウィンドウ内のプロットのレイアウト。デフォルト: `(1, 1)`
  * `size`: プロットウィンドウの解像度。デフォルト: `(500, 500)`
  * `legend`: 凡例（位置）：[:none, :best, :lt, :ct, :rt, :lc, :rc, :lb, :cb, :rb]のいずれか。デフォルト: `none`
  * `title`: プロットのタイトル。デフォルト: ``
  * `xlabel`: x軸のラベル。デフォルト: `x`
  * `ylabel`: y軸のラベル。デフォルト: `y`
  * `zlabel`: z軸のラベル。デフォルト: `z`
  * `xlimits`: x軸の制限。デフォルト: `(1, -1)`
  * `ylimits`: y軸の制限。デフォルト: `(1, -1)`
  * `zlimits`: z軸の制限。デフォルト: `(1, -1)`
  * `limits`: 関数の制限。デフォルト: `(1, -1)`
  * `xscale`: x軸のスケール：[:log, :identity]のいずれか。デフォルト: `identity`
  * `yscale`: y軸のスケール：[:log, :identity]のいずれか。デフォルト: `identity`
  * `aspect`: XYアスペクト比の修正。デフォルト: `1.0`
  * `fontsize`: タイトルのフォントサイズ。他はすべてこれに対して相対的です。デフォルト: `20`
  * `linewidth`: 等高線または1Dプロットの線幅。デフォルト: `2`
  * `linestyle`: 1Dプロットの線スタイル：[:solid, :dash, :dot, :dashdot, :dashdotdot]のいずれか。デフォルト: `solid`
  * `markevery`: 1Dプロットのマーカーの間隔。デフォルト: `5`
  * `markersize`: 1Dプロットのマーカーサイズ。デフォルト: `5`
  * `markershape`: 1Dプロットのマーカー形状：[:none, :circle, :star5, :diamond, :hexagon, :cross, :xcross, :utriangle, :dtriangle, :rtriangle, :ltriangle, :pentagon, :+, :x]のいずれか。デフォルト: `none`
  * `color`: 1Dプロットの線の色。デフォルト: `(0.0, 0.0, 0.0)`
  * `cellwise`: 1Dプロットをセル単位で（メンテナンスされておらず、遅くなる可能性があります）。デフォルト: `false`
  * `label`: 1Dプロットのラベル。デフォルト: ``
  * `levels`: 等高線プロットの等高線の配列または数。デフォルト: `5`
  * `elevation`: 2Dプロットの高さ係数。デフォルト: `0.0`
  * `colorlevels`: 2D/3D等高線プロット：色のレベルの数。デフォルト: `51`
  * `colormap`: 2D/3D等高線プロットのカラーマップ（[ColorSchemes.jl](https://juliagraphics.github.io/ColorSchemes.jl/stable/basics/#Pre-defined-schemes)からの任意のもの）。デフォルト: `viridis`
  * `colorbar`: 2D/3Dプロットのカラーバー。[:none, :vertical, :horizontal]のいずれか。デフォルト: `vertical`
  * `colorbarticks`: カラーバーの目盛りの数（:defaultはそれをlevelsと等しく設定します）。デフォルト: `default`
  * `outlinealpha`: 3Dアウトライン表面のアルファ値。デフォルト: `0.05`
  * `levelalpha`: 3D等高線のアルファ。デフォルト: `0.25`
  * `planealpha`: 3D平面セクションのアルファ。デフォルト: `1.0`
  * `spacing`: ベクトルプロットにおけるクイバーポイントの間隔。デフォルト: `default`
  * `offset`: クイバーグリッドのオフセット。デフォルト: `default`
  * `vscale`: クイバーグリッドのベクトルフィールドスケール。デフォルト: `1.0`
  * `vnormalize`: スケーリングの前にベクトルフィールドを正規化します。デフォルト: `true`
  * `interior`: 3Dプロットのグリッドの内部。デフォルト: `true`
  * `xplanes`: 3D x平面の位置またはその数。デフォルト: `[1.7976931348623157e308]`
  * `yplanes`: 3D y平面の位置またはその数。デフォルト: `[1.7976931348623157e308]`
  * `zplanes`: 3D z平面の位置またはその数。デフォルト: `[1.7976931348623157e308]`
  * `zoom`: ズームレベル。デフォルト: `1.0`
  * `gridscale`: グリッドスケールファクター。デフォルト: `1.0`
  * `azim`: 3D方位角（度単位）。デフォルト: `-60`
  * `elev`: 3D標高角（度単位）。デフォルト: `30`
  * `perspectiveness`: 3Dの視点。0と1の間の数値で、0は正投影、1は完全な透視です。デフォルト: `0.25`
  * `scene3d`: 3DプロットのMakieシーンのタイプ。`Axis3`の代替は`LScene`です。デフォルト: `Axis3`
  * `fignumber`: 図の番号（PyPlot）。デフォルト: `1`
  * `framepos`: フレーム内のサブプロットの位置（VTKView）。デフォルト: `1`
  * `subplot`: プライベート：実際のサブプロット。デフォルト: `(1, 1)`
  * `backend`: PlutoVistaプロットのバックエンド。デフォルト: `default`
  * `dim`: PlutoVistaプロットのデータ次元。デフォルト: `1`
  * `regions`: プロットする領域のリスト。デフォルト: `all`
  * `species`: プロットする種の数または領域内の種の数。デフォルト: `1`
