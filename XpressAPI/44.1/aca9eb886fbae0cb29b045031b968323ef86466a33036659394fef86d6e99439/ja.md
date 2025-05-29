```
XPRSgetobjdblattrib(prob, solveidx, attrib)::value
```

与えられたダブル属性の値を取得します。これはマルチオブジェクティブソルブに関連しています。

マルチオブジェクティブ問題を解決する際、いくつかの目的が順番に最適化されることがあります。各解決後、問題の属性がキャプチャされ、その後クエリできるようになります。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `solveidx::Integer`: クエリする解のインデックス。
  * `attrib::Integer`: 値を返す問題属性。

# 戻り値

  * `value::Float64`: 属性値が返されるダブルへのポインタ。

C APIの対応する関数[XPRSgetobjdblattrib](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetobjdblattrib.html)のドキュメントも参照してください。
