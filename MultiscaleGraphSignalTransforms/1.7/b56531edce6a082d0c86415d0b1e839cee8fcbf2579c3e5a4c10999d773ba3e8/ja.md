```
gplot(A, xyz; plotp = true,
      style = :auto, width = 2, color = :blue,
      shape = :none, mwidth = 2, mcolor = color, malpha = 1.0,
      mscolor = color, mswidth = 1, msalpha = 1.0,
      grid::Bool = false, label = "", subplot = 1)
```

GPLOT グラフ理論におけるグラフをプロットします。 GPLOT(A,xyz,...) は隣接行列 A とノード座標 xyz によって指定されたグラフをプロットします。 GPLOT!(A,xyz,...) は `current` にプロットを追加します。

### 入力引数

  * `A::SparseMatrixCSC{Float64,Int}`: グラフ `G` の隣接行列
  * `xyz::Matrix{Float64}`: 座標配列 `xyz` は n 行 2 列または n 行 3 列の行列で、ノード i の位置は i 行目にあり、xyz[i,:] = [x[i] y[i]] または xyz[i,:] = [x[i] y[i] z[i]] です。
  * `plotp::Bool`: プロットが作成されるか (デフォルト) または X, Y, Z 配列を返すか
  * `style::Symbol`: 線のスタイル; Symbol[:auto,:solid,:dash,:dot,:dashdot] から選択 (デフォルト: :auto)
  * `width::Number`: ピクセル単位の線の幅 (デフォルト: 2; 分数、例: 0.5 も許可)
  * `color::Symbol`: 線の色; Symbol[:white,:blue,:red,:green,...] から選択 (デフォルト: :blue)
  * `shape::Symbol`: Symbol[:none,:auto,:circle,:rect,:star5,:diamond,                                     :hexagon,:cross,:xcross,:utriangle,                                     :dtriangle,:pentagon,:heptagon,:octagon,                                     :star4,:star6,:star7,:star8,:vline,:hline] から選択 (デフォルト: :none)
  * `mwidth::Number`: マーカーのサイズ (または半径) ピクセル単位 (デフォルト: 2)
  * `mcolor::Symbol`: マーカーの色 (デフォルト: 線の色と同じ)
  * `malpha::Float64`: マーカー内部の不透明度; [0,1] から選択 (デフォルト: 1.0)
  * `mswidth::Number`: マーカーのストロークサイズ (幅) ピクセル単位 (デフォルト: 1)
  * `mscolor::Symbol`: マーカーのストロークの色 (デフォルト: 線の色と同じ)
  * `msalpha::Float64`: マーカーのストロークの不透明度; [0,1] から選択 (デフォルト: 1.0)
  * `grid::Bool`: グリッド線を表示するフラグ (デフォルト: false)
  * `label::String`: 凡例用の文字列 (デフォルト: "")
  * `subplot::Int`: サブプロットインデックス (デフォルト: 1)

### 出力引数

  * `X::Matrix{Float64}`: NaN で区切られた X 座標ベクトル
  * `Y::Matrix{Float64}`: NaN で区切られた Y 座標ベクトル
  * `Z::Matrix{Float64}`: NaN で区切られた Z 座標ベクトル

(X,Y)= GPLOT(A,xyz,plotp=false,...) または (X,Y,Z) = GPLOT(A,xyz,plotp=false,...) は、実際にプロットを生成することなく NaN で区切られたベクトル X と Y または X, Y と Z を返します。これらのベクトルは、必要に応じて後で PLOT または PLOT3D でプロットを生成するために使用できます。

Mathworks の gplot の後方互換性のある拡張で、プロットが回転するときに 3D データ (利用可能な場合) を使用します。ロバート・ピシェ、タンペレ工科大学、2005年

ナオキ・サイトウによって 2016年12月21日に Julia に翻訳されました。キーワードは `function gplot(A,xyz,kw...)` として整理されるべきであることに注意してください。

ニコラス・ハウシュ編集: Plots パッケージをインストールする必要があります。3D 回転には `plotlyjs()` バックエンドを使用します。

ナオキ・サイトウによって改訂、2017年2月17日 ナオキ・サイトウによって改訂、2017年10月13日 ハオティアン・リーによって改訂、2018年7月25日 ハオティアン・リーとナオキ・サイトウによって Julia v0.7/1.0 用に改訂、2018年9月21日 plot(...) の代わりに Plots.plot(...) を使用することに決定しました。これは関数名の曖昧さを避けるための安全なアプローチです。ナオキ・サイトウによって改訂、2018年10月22日
