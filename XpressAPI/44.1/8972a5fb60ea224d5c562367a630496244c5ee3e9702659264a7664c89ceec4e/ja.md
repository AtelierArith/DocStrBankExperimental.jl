```
XPRSdelobj(prob, objidx)::prob
```

マルチオブジェクティブ問題から目的関数を削除します。

`index > objidx` の目的は下にシフトされます。問題内の最後の目的関数を削除すると、すべての目的係数がゼロになりますが、`OBJECTIVES` は `1` に設定されたままです。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `objidx::Integer`: 削除する目的のインデックス。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数 [XPRSdelobj](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelobj.html) のドキュメントも参照してください。
