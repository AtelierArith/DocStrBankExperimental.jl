```
XPRSslpchgrowstatus(prob, row)::status
```

制約のステータス設定を変更します

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 変更する行列の行のインデックス。

# 戻り値

  * `status::Int32`: 新しいステータス設定を持つビットマップを保持する整数のアドレス。

C APIの対応する関数[XPRSslpchgrowstatus](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSslpchgrowstatus.html)のドキュメントも参照してください。
