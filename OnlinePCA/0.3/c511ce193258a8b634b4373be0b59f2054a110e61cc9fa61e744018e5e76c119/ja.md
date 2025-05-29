```
hvg(;binfile::AbstractString="", rowmeanlist::AbstractString="", rowvarlist::AbstractString="", rowcv2list::AbstractString="", outdir::AbstractString=".")
```

この関数は、scRNA-seq研究における特徴選択手法である高変動遺伝子を実行します。

## 入力引数

  * `binfile` は `csv2bin` 関数によって生成されたJuliaバイナリファイルです。
  * `rowmeanlist` : 行列の各行の平均。CSVファイルは `sumr` 関数によって生成されます。
  * `rowvarlist` : 行列の各行の分散。CSVファイルは `sumr` 関数によって生成されます。
  * `rowcv2list` : 行列の各行のcv2。CSVファイルは `sumr` 関数によって生成されます。
  * `outdir` : 結果を保存したいディレクトリを指定します。

## 出力ファイル

  * `HVG_useForFit.csv` : 高変動遺伝子を推定するためのパラメータ。
  * `HVG_a0.csv` : 高変動遺伝子を推定するためのパラメータ。
  * `HVG_a1.csv` : 高変動遺伝子を推定するためのパラメータ。
  * `HVG_afits.csv` : 高変動遺伝子を推定するためのパラメータ。
  * `HVG_varFitRatio.csv` : 高変動遺伝子を推定するためのパラメータ。
  * `HVG_df.csv` : 高変動遺伝子を推定するためのパラメータ。
  * `HVG_pval.csv` : 高変動遺伝子を推定するためのパラメータ。

## 参考文献

  * [Highly Variable Genes](http://pklab.med.harvard.edu/scw2014/subpop_tutorial.html)
