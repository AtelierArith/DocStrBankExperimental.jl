GetVisitDate(visit*occurrence*id; interval::Symbol = :start, tab = visit_occurrence)

この関数は、指定された `visit_occurrence_id` または `visit_occurrence_id` のリストに関連付けられた訪問の開始日または終了日をデータベースに問い合わせます。

# 引数:

  * `visit_occurrence_id`: 問い合わせる単一の `visit_occurrence_id` または `visit_occurrence_id` のベクター。
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数

  * `interval`: 訪問の開始日を問い合わせるか (`interval=:start`)、訪問の終了日を問い合わせるか (`interval=:end`) を決定するキーワード引数。デフォルト値は `interval=:start` です。

# 戻り値:

`visit_occurrence_id` と `visit_start_date` または `visit_end_date` のいずれかの2列を持つデータフレーム。これは `interval` 引数の値に応じて異なります。
