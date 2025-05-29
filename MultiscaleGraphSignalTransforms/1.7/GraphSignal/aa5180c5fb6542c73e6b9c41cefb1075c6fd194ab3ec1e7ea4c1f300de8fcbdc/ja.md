```
G = GraphSig(W, xy, f, name, plotspecs, length, dim, size)
```

は、以下のフィールドを含むGraphSigオブジェクトのデータ構造です：

  * `W::SparseMatrixCSC{Float64,Int}`: スパース形式のエッジ重み行列
  * `xy::Matrix{Float64}`: 頂点の座標（3D以上の可能性あり）
  * `f::Matrix{Float64}`: 頂点での関数/データの値；各列は入力信号ベクトルであり、すなわち行数 == ノード数。
  * `name::String`: データのタイトル/名前
  * `plotspecs::Vector{Symbol}`: プロットの仕様：   (julia/Plots.jlのおかげで後で削除される可能性が高い)                  - symm: 対称的なカラースケールを使用                  - gray: グレースケールを使用                  - gray255: カラーバウンド[0,255]でグレースケール画像をプロット                  - copper: 銅のカラースケールを使用                  - notitle: タイトルを表示しない                  - nocolorbar: カラーバーを表示しない                  - stem: ステムプロットを使用                  - CLim[cmin,cmax]: 動的表示範囲を[cmin,cmax]に設定                  - size25: ノードのサイズを25に設定（または指定された任意の値）                  - LineWidth2: 線の幅を2に設定（または指定された任意の値）                  - LineColorb: 線/グラフエッジの色を色'b'に設定（または指定された任意の色）                  - red/black/blue: ノードを赤、黒、または青にする                  - verbatim{{...}}: 括弧内のコマンドを実行する

```
