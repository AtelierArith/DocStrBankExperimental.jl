任意のエラー最小化探索 (AEMS) を実装します。具体的には、AEMS1 よりも一般的に優れた AEMS2 です。

いくつかのオプション引数を使用した例：

`AEMSSolver(max_iterations = 100, action_selector = :L)`

フィールド：

  * `max_iterations`   アクションごとの最大ノード拡張数。
  * `max_time`   アクションごとに費やす最大時間（秒単位）。
  * `updater`   信念ノードを伝播させるために使用されるアップデーター。デフォルトは DiscreteUpdater。
  * `lower_bound`   `Policy` のサブタイプ。デフォルトは固定アクションポリシー。
  * `upper_bound`   `Policy` のサブタイプ。デフォルトは FIB ポリシー。
  * `root_manager`   許可される値は `:clear`、`:belief`、または `:user` です。デフォルトは `:clear`。
  * `action_selector`   許可される値は `:U` または `:L` です。デフォルトは `:U`。
