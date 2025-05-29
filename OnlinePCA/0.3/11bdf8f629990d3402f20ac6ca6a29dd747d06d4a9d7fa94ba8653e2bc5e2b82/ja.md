```
sumr(; binfile::AbstractString="", outdir::AbstractString=".", pseudocount::Number=1.0, mode::AbstractString="dense", chunksize::Int=1)
```

データ行列の要約情報を抽出します。

## 入力引数

  * `binfile` は `csv2bin` 関数によって生成された Julia バイナリファイルです。
  * `outdir` は結果を保存したいディレクトリを指定します。
  * `pseudocount` は log10(0) による NaN を避けるために指定され、`Feature_LogMeans.csv` <log10(mean+pseudocount) 各特徴の値> が生成されるときに使用されます。
  * `mode` : "dense" または "sparse_mm" を指定できます。
  * `chunksize` : 一度に読み込む行数です。

## 出力ファイル

  * `Sample_NoCounts.csv` : 各列のカウントの合計。
  * `Feature_Means.csv` : 各行の平均。
  * `Feature_LogMeans.csv` : 各行の Log10(Mean+pseudocount)。
  * `Feature_FTTMeans.csv` : 各行の FTT(Mean+pseudocount)。
  * `Feature_Vars.csv` : 各行のサンプル分散。
  * `Feature_LogVars.csv` : 各行の Log10(Var+pseudocount)。
  * `Feature_FTTVars.csv` : 各行の FTT(Var+pseudocount)。
  * `Feature_CV2s.csv` : 各行の変動係数。
  * `Feature_NoZeros.csv` : 各行のゼロ要素の数。
