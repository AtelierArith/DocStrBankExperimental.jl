```
filtering(;input::AbstractString="", featurelist::AbstractString="", samplelist::AbstractString="", thr1::Number=0.0, thr2::Number=0.0, direct1::AbstractString="+", direct2::AbstractString="+", outdir::AbstractString=".")
```

この関数は、遺伝子の平均や分散などの基準に基づいて遺伝子をフィルタリングします。

## 入力引数

  * `input` : `csv2bin` 関数によって生成された Julia バイナリファイル。
  * `featurelist` : 行ごとの要約データ。CSVファイルは `csv2bin` 関数によって生成されます。
  * `thr` : 低信号特徴を拒否するための閾値。
  * `outdir` : 結果を保存したいディレクトリを指定します。

## 出力ファイル

  * `filtered.zst` : フィルタリングされたバイナリファイル。
