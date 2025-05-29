```
XPRSsetmessagestatus(prob, msgcode, status)::prob
```

メッセージの抑制を管理します。

# 引数

  * `prob::XPRSprob`: メッセージ `msgcode` の抑制状態を変更する問題; メッセージがすべての問題に対してグローバルに適用されるべきであれば `nothing` を渡します。
  * `msgcode::Integer`: メッセージのID番号。
  * `status::Integer`: メッセージが抑制されていない場合は非ゼロ; それ以外の場合は `0`。コマンドライン呼び出しで `status` の値が指定されていない場合、コンソールオプティマイザは抑制状態の値を画面に表示します。すなわち、メッセージが抑制されていない場合は非ゼロ; それ以外の場合は `0`。

# 戻り値

  * `prob::XPRSprob`: メッセージ `msgcode` の抑制状態を変更する問題; メッセージがすべての問題に対してグローバルに適用されるべきであれば `nothing` を渡します。

対応する関数 [XPRSsetmessagestatus](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSsetmessagestatus.html) のドキュメントも参照してください。
