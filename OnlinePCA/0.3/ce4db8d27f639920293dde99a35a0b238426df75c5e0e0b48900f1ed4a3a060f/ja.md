```
oja(;input::AbstractString="", outdir::Union{Nothing,AbstractString}=nothing, scale::AbstractString="ftt", pseudocount::Number=1f0, rowmeanlist::AbstractString="", rowvarlist::AbstractString="", colsumlist::AbstractString="", dim::Number=3, stepsize::Number=0.1, numepoch::Number=3, scheduling::AbstractString="robbins-monro", g::Number=0.9, epsilon::Number=1.0e-8, lower::Number=0, upper::Number=1.0f+38, expvar::Number=0.1f0, evalfreq::Number=5000, offsetFull::Number=1f-20, offsetStoch::Number=1f-6, initW::Union{Nothing,AbstractString}=nothing, initV::Union{Nothing,AbstractString}=nothing, logdir::Union{Nothing,AbstractString}=nothing, perm::Bool=false, cper::Number=1f0)
```

オヤの方法。

## 入力引数

  * `input` : `OnlinePCA.csv2bin` 関数によって生成された Julia バイナリファイル。
  * `outdir` : 結果を保存したいディレクトリを指定します。
  * `scale` : 値のスケーリング {log,ftt,raw}。
  * `pseudocount` : log10(0)によるNaNを避けるために指定された数値で、`Feature_LogMeans.csv` <log10(mean+pseudocount) 各特徴の値> が生成されるときに使用されます。
  * `rowmeanlist` : 行列の各行の平均。CSVファイルは `OnlinePCA.sumr` 関数によって生成されます。
  * `rowvarlist` : 行列の各行の分散。CSVファイルは `OnlinePCA.sumr` 関数によって生成されます。
  * `colsumlist` : 行列の各列のカウントの合計。CSVファイルは `OnlinePCA.sumr` 関数によって生成されます。
  * `dim` : PCAの次元数。
  * `stepsize` : 各イテレーションで使用されるパラメータ。
  * `numepoch` : エポックの数。
  * `scheduling` : 学習パラメータのスケジューリング。`robbins-monro`、`momentum`、`nag`、および `adagrad` が利用可能です。
  * `g` : スケジューリングがnagとして指定されたときに使用されるパラメータ。
  * `epsilon` : スケジューリングがadagradとして指定されたときに使用されるパラメータ。
  * `lower` : 停止基準（エラーの相対変化がこの値を下回ると計算が終了します）
  * `upper` : 停止基準（エラーの相対変化がこの値を上回ると計算が終了します）
  * `evalfreq` : 再構成誤差の評価頻度
  * `offsetFull` : フル勾配を計算する際のオーバーフローを避けるためのオフセット値
  * `offsetStoch` : 確率的勾配を計算する際のオーバーフローを避けるためのオフセット値
  * `initW` : 固有ベクトルの初期値を保存するCSVファイル。
  * `initV` : ローディングの初期値を保存するCSVファイル。
  * `logdir` : 各 evalfreq（例：5000）イテレーションで中間ファイルが保存されるディレクトリ。
  * `perm` : データ行列がランダムにシャッフルされるかどうか。
  * `cper` : Xあたりのカウント（例：CPM: 百万あたりのカウント <1e+6>）

## 出力引数

  * `W` : 共分散行列の固有ベクトル（データ行列の列数 × dim）
  * `λ` : 固有値（dim × dim）
  * `V` : 共分散行列のローディングベクトル（データ行列の行数 × dim）
  * `Scores` : 主成分スコア
  * `ExpVar` : 固有ベクトルによって説明される分散
  * `TotalVar` : データ行列の総分散
  * stop : 計算が収束したかどうか

## 参考文献

  * SGD-PCA（オヤの方法）: [Erkki Oja et. al., 1985](https://www.sciencedirect.com/science/article/pii/0022247X85901313), [Erkki Oja, 1992](https://www.sciencedirect.com/science/article/pii/S0893608005800899)
