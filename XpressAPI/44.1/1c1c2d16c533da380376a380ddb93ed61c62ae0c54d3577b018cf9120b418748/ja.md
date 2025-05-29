```
XPRSgetmessagestatus(prob, msgcode)::status
```

メッセージの現在の抑制状態を取得します。

# 引数

  * `prob::XPRSprob`: メッセージエラーコードの抑制状態を確認する問題。
  * `msgcode::Integer`: メッセージのID番号。

# 戻り値

  * `status::Int32`: メッセージが抑制されていない場合は非ゼロ; それ以外の場合は `0`。

C APIの対応する関数のドキュメント [XPRSgetmessagestatus](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetmessagestatus.html) も参照してください。
