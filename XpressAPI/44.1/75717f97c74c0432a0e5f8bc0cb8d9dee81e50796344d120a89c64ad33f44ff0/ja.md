```
XPRSslpgetcolinfoint(prob, type, col)::info
```

現在の列情報を取得します。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題
  * `type::Integer`: 情報のタイプ（以下を参照）
  * `col::Integer`: 情報を処理する列のインデックス

# 戻り値

  * `info::Int32`: 設定または取得される情報のアドレス

対応する関数[XPRSslpgetcolinfo](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpgetcolinfo.html)のC APIのドキュメントも参照してください。
