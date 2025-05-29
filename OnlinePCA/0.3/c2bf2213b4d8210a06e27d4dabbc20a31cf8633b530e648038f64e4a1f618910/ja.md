```
exact_ooc_pca(; input::AbstractString="", outdir::Union{Nothing,AbstractString}=nothing, scale::AbstractString="raw", pseudocount::Number=1.0f0, dim::Number=3, chunksize::Number=1, mode::AbstractString="dense")
```

正確なアウトオブコアPCAは、通常のフルランクSVDに基づいており、低ランク近似を仮定しません。

## 入力引数

  * `input` : `OnlinePCA.csv2bin`または`OnlinPCA.mm2bin`関数によって生成されたJuliaバイナリファイル。
  * `outdir` : 結果を保存したいディレクトリを指定します。
  * `scale` : 値の{raw,log,ftt}スケーリング。
  * `pseudocount` : log10(0)によるNaNを避けるために指定された数値で、`Feature_LogMeans.csv` <log10(mean+pseudocount) 各特徴の値>が生成されるときに使用されます。
  * `dim` : PCAの次元数。
  * `chunksize` : 一度に読み込む行数。
  * `mode` : "dense"、"sparse*mm"、または"sparse*bincoo"を指定できます。

## 出力引数

  * `V` : 共分散行列の固有ベクトル（データ行列の列数 × dim）
  * `λ` : 固有値（dim × dim）
  * `U` : 共分散行列のローディングベクトル（データ行列の行数 × dim）
  * `Scores` : 主成分スコア
  * `ExpVar` : 固有ベクトルによって説明される分散
  * `TotalVar` : データ行列の総分散
