```
sparse_rsvd(; input::AbstractString="", outdir::Union{Nothing,AbstractString}=nothing, scale::AbstractString="ftt", rowmeanlist::AbstractString="", rowvarlist::AbstractString="", colsumlist::AbstractString="", dim::Number=3, noversamples::Number=5, niter::Number=3, chunksize::Number=1, initW::Union{Nothing,AbstractString}=nothing, initV::Union{Nothing,AbstractString}=nothing, logdir::Union{Nothing,AbstractString}=nothing, perm::Bool=false, cper::Number=1.0f0)
```

ランダム化SVD。

## 入力引数

  * `input` : `OnlinePCA.mm2bin`関数によって生成されたJuliaバイナリファイル。
  * `outdir` : 結果を保存したいディレクトリを指定します。
  * `scale` : {ftt,log,raw} - 値のスケーリング。
  * `rowmeanlist` : 行列の各行の平均。CSVファイルは`OnlinePCA.sumr`関数によって生成されます。
  * `rowvarlist` : 行列の各行の分散。CSVファイルは`OnlinePCA.sumr`関数によって生成されます。
  * `colsumlist` : 行列の各列のカウントの合計。CSVファイルは`OnlinePCA.sumr`関数によって生成されます。
  * `dim` : PCAの次元数。
  * `noversamples` : オーバーサンプリングの数。
  * `niter` : パワー反復の数。
  * `chunksize` : 一度に読み込む行の数（例：1）。
  * `initW` : 固有ベクトルの初期値を保存するCSVファイル。
  * `initV` : ローディングの初期値を保存するCSVファイル。
  * `logdir` : 中間ファイルが保存されるディレクトリ、各evalfreq（例：1）反復で。
  * `perm` : データ行列がランダムにシャッフルされるかどうか。
  * `cper` : Xあたりのカウント（例：CPM：百万あたりのカウント <1e+6>）

## 出力引数

  * `V` : 共分散行列の固有ベクトル（データ行列の列数 × dim）
  * `λ` : 固有値（dim × dim）
  * `U` : 共分散行列のローディングベクトル（データ行列の行数 × dim）
  * `Scores` : 主成分スコア
  * `ExpVar` : 固有ベクトルによって説明される分散
  * `TotalVar` : データ行列の総分散

```
