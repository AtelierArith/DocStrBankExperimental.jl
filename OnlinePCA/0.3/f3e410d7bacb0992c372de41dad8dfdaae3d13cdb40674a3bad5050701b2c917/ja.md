```
tenxsumr(; tenxfile::AbstractString="", outdir::AbstractString=".", group::AbstractString="", chunksize::Number=5000)
```

10X-HDF5の要約情報を抽出します。

## 入力引数

  * `tenxfile` は10X GenomicsによってフォーマットされたHDF5ファイルです。
  * `outdir` は結果を保存したいディレクトリを指定します。
  * `group` はHDF5のグループ名です（例：mm10）。
  * `chunksize` は一度に読み込む行数です（例：5000）。

## 出力ファイル

  * `Sample_NoCounts.csv` : 各列のカウントの合計。
  * `Feature_Means.csv` : 各行の平均。
  * `Feature_LogMeans.csv` : 各行のLog10(Mean+1)。
  * `Feature_SqrtMeans.csv` : 各行のsqrt(Mean+1)。
  * `Feature_Vars.csv` : 各行のサンプル分散。
  * `Feature_LogVars.csv` : 各行のLog10(Var+1)。
  * `Feature_SqrtVars.csv` : 各行のsqrt(Var+1)。
  * `Feature_CV2s.csv` : 各行の変動係数。
