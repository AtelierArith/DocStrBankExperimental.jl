```
struct JetTrim
```

ジェットからのソフトで大きな角度の成分を、フラクションと半径に基づいてトリミングします。

# フィールド:

  * `trim_radius::Float64`: トリミング時の再クラスタリングに使用される半径。
  * `trim_fraction::Float64`: 残されたサブジェットのための最小運動量フラクション。
  * `recluster_method::JetAlgorithm.Algorithm`: 再クラスタリングのためのメソッド識別子。
