```
XPRSreadprob(prob, filename, flags)::prob
```

ファイルから (X)MPS または LP 形式の行列を読み込みます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `filename::Union{Nothing,AbstractString}`: 問題を読み込むためのパスとファイル名。
  * `flags::Union{Nothing,AbstractString}`: 渡すフラグ: lonly `filename.lp` が検索される; vuse 提供されたファイル名をそのまま使用し、`.mps`、`.mat` または `.lp` 拡張子を追加しない; zread 圧縮された入力ファイル。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSreadprob](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSreadprob.html) のドキュメントも参照してください。
