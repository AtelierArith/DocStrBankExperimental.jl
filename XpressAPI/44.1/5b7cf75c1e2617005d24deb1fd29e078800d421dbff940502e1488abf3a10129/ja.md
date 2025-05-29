```
XPRSslpgetrowinfoint(prob, type, row)::info
```

現在の行情報を取得します。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題
  * `type::Integer`: 情報のタイプ（下記参照）
  * `row::Integer`: 情報を処理する行のインデックス

# 戻り値

  * `info::Int32`: 設定または取得される情報のアドレス

対応する関数のドキュメント [XPRSslpgetrowinfo](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetrowinfo.html) をC APIで参照してください。
