```
Scheduler{TSolution <: Solution}
```

メタヒューリスティクスのための型で、特定のメソッド/操作を反復的に適用することによって機能します。

# 要素

  * `incumbent`: 現在の解、すなわち初期解であり、これまでに遭遇した中で常に最良の解
  * `incumbent_valid`: `true`の場合、incumbentは考慮すべき有効な解である
  * `incumbent_iteration`: incumbentが見つかった反復
  * `incumbent_time`: incumbentが見つかった時刻
  * `methods`: すべての`MHMethods`のベクター
  * `method_stats`: 各`MHMethod`のための`MHMethodStatistics`の辞書
  * `iteration`: メソッドの適用の総数
  * `time_start`: アルゴリズムの開始時刻
  * `run_time`: 総実行時間（終了時に設定される）
  * `params`: デフォルトで設定から採用されたパラメータ
