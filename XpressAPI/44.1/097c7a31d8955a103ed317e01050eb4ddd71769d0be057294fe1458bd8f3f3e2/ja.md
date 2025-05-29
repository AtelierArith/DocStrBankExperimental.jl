```
XPRSgetobjintattrib64(prob, solveidx, attrib)::value
```

与えられた整数属性の値をマルチオブジェクティブソルブに関連付けて取得します。

マルチオブジェクティブ問題を解決する際、いくつかの目的が順番に最適化されることがあります。各解決後、問題の属性がキャプチャされ、その後クエリできるようになります。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `solveidx::Integer`: クエリする解のインデックス。
  * `attrib::Integer`: 値を返す問題属性。

# 戻り値

  * `value::Int64`: 属性値が返される整数へのポインタ。

C APIの対応する関数[XPRSgetobjintattrib64](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetobjintattrib64.html)のドキュメントも参照してください。
