```
arnoldi(;input::AbstractString="", outdir::Union{Nothing,AbstractString}=nothing, scale::AbstractString="ftt", pseudocount::Number=1f0, rowmeanlist::AbstractString="", rowvarlist::AbstractString="",colsumlist::AbstractString="", dim::Number=3, numepoch::Number=10, perm::Bool=false, cper::Number=1f0)
```

アーノルディ法。

## 入力引数

  * `input` : `OnlinePCA.csv2bin` 関数によって生成された Julia バイナリファイル。
  * `outdir` : 結果を保存したいディレクトリを指定します。
  * `scale` : {log,ftt,raw} - 値のスケーリング。
  * `pseudocount` : log10(0) による NaN を避けるために指定された数値で、`Feature_LogMeans.csv` <各特徴の log10(mean+pseudocount) 値> が生成されるときに使用されます。
  * `rowmeanlist` : 行列の各行の平均。CSV ファイルは `OnlinePCA.sumr` 関数によって生成されます。
  * `rowvarlist` : 行列の各行の分散。CSV ファイルは `OnlinePCA.sumr` 関数によって生成されます。
  * `colsumlist` : 行列の各列のカウントの合計。CSV ファイルは `OnlinePCA.sumr` 関数によって生成されます。
  * `dim` : PCA の次元数。
  * `perm` : データ行列がランダムにシャッフルされるかどうか。
  * `cper` : X あたりのカウント (例: CPM: 百万あたりのカウント <1e+6>)

## 出力引数

  * `W` : 共分散行列の固有ベクトル (データ行列の列数 × dim)
  * `λ` : 固有値 (dim × dim)
  * `V` : 共分散行列のローディングベクトル (データ行列の行数 × dim)
  * `Scores` : 主成分スコア
  * `ExpVar` : 固有ベクトルによって説明される分散
  * `TotalVar` : データ行列の総分散
  * stop : 計算が収束したかどうか
