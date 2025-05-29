```
XPRSslpgetcolinfodouble(prob, type, col)::info
```

現在の列情報を取得します。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題
  * `type::Integer`: 情報のタイプ（下記参照）
  * `col::Integer`: 情報を処理する列のインデックス

# 戻り値

  * `info::Float64`: 設定または取得される情報のアドレス

対応する関数のドキュメント [XPRSslpgetcolinfo](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetcolinfo.html) をC APIで参照してください。
