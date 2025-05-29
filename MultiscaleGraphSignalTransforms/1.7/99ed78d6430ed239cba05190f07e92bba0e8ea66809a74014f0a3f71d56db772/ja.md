```
GraphSig_Plot(G::GraphSig; symmetric::Bool = false,
  markersize::Float64 = 2.,
  markercolor::Symbol = :balance,
  markershape::Symbol = :circle,
  markerstrokewidth::Float64 = 1.0,
  markerstrokealpha::Float64 = 1.0,
  markervaluevaries::Bool = true,
  linewidth::Float64 = 1.,
  linecolor::Symbol = :blue,
  linestyle::Symbol = :solid,
  clim::Tuple{Float64,Float64} = (0., 0.),
  notitle::Bool = false, nocolorbar::Bool = false, nolegend::Bool = true,
  stemplot::Bool = false, sortnodes::Symbol = :normal)
```

GraphSigオブジェクトのデータのプロットを表示します

### 入力引数

  * `G::GraphSig`:        入力GraphSigオブジェクト
  * `symmetric`           カラーバーを対称化する
  * `markersize`          ノードのサイズ
  * `markercolor`         マーカーのカラースキーム
  * `markershape`         マーカーの形状
  * `markerstrokewidth`   マーカーのストロークの幅
  * `markerstrokealpha`   マーカーのストロークの透明度
  * `markervaluevaries`   マーカーの色が信号値に依存するかどうか
  * `linewidth`           gplotの線の幅
  * `linecolor`           線の色（1D）/ グラフのエッジ（2D & 3D）
  * `linestyle`:          線のスタイル
  * `notitle`             タイトルを表示する
  * `nocolorbar`          カラーバーを表示しない
  * `nolegend`            凡例を表示しない
  * `stemplot`            ステムプロットを使用する
  * `clim`                動的表示範囲を指定する
  * `sortnodes`           信号値を絶対値の小さい順から大きい順にプロットする
