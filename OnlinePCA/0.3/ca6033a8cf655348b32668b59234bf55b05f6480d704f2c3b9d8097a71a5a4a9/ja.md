```
rbkiter(;input::AbstractString="", outdir::Union{Nothing,AbstractString}=nothing, scale::AbstractString="ftt", pseudocount::Number=1f0, rowmeanlist::AbstractString="", rowvarlist::AbstractString="",colsumlist::AbstractString="", dim::Number=3, numepoch::Number=10, lower::Number=0, upper::Number=1.0f+38, expvar::Number=0.1f0, initW::Union{Nothing,AbstractString}=nothing, initV::Union{Nothing,AbstractString}=nothing, logdir::Union{Nothing,AbstractString}=nothing, perm::Bool=false, cper::Number=1f0)
```

ランダム化ブロッククリロフ反復法。

## 入力引数

  * `input` : `OnlinePCA.csv2bin` 関数によって生成されたJuliaバイナリファイル。
  * `outdir` : 結果を保存したいディレクトリを指定します。
  * `scale` : {log,ftt,raw} - 値のスケーリング。
  * `pseudocount` : log10(0)によるNaNを避けるために指定された数値で、`Feature_LogMeans.csv` <log10(mean+pseudocount) 各特徴の値> が生成されるときに使用されます。
  * `rowmeanlist` : 行列の各行の平均。CSVファイルは `OnlinePCA.sumr` 関数によって生成されます。
  * `rowvarlist` : 行列の各行の分散。CSVファイルは `OnlinePCA.sumr` 関数によって生成されます。
  * `colsumlist` : 行列の各列のカウントの合計。CSVファイルは `OnlinePCA.sumr` 関数によって生成されます。
  * `dim` : PCAの次元数。
  * `numepoch` : エポック数。
  * `lower` : 停止基準（誤差の相対変化がこの値を下回ると計算が終了します）
  * `upper` : 停止基準（誤差の相対変化がこの値を上回ると計算が終了します）
  * `initW` : 固有ベクトルの初期値を保存するCSVファイル。
  * `initV` : ローディングの初期値を保存するCSVファイル。
  * `logdir` : 中間ファイルが保存されるディレクトリ、各evalfreq（例：5000）反復ごとに。
  * `perm` : データ行列がランダムにシャッフルされるかどうか。
  * `cper` : Xあたりのカウント（例：CPM：百万あたりのカウント <1e+6>）

## 出力引数

  * `W` : 共分散行列の固有ベクトル（データ行列の列数 × dim）
  * `λ` : 固有値（dim × dim）
  * `V` : 共分散行列のローディングベクトル（データ行列の行数 × dim）
  * `Scores` : 主成分スコア
  * `ExpVar` : 固有ベクトルによって説明される分散
  * `TotalVar` : データ行列の総分散
  * stop : 計算が収束したかどうか
