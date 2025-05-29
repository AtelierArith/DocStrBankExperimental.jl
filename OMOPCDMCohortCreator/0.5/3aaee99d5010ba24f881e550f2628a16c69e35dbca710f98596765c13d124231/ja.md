GetVisitDate(visit*occurrence*id; interval::Symbol = :start, tab = visit_occurrence)

与えられた訪問IDのリストに基づいて、訪問の開始日または終了日を見つけるSQL文を生成します。

# 引数:

  * `visit_occurrence_id`: クエリする単一の `visit_occurrence_id` または `visit_occurrence_id` のベクター。

# キーワード引数

  * `interval`: 訪問の開始日をクエリするか (`interval=:start`) 訪問の終了日をクエリするかを決定するキーワード引数。デフォルト値は `interval=:start` です。

# 戻り値:

2つの列を持つデータフレーム: `visit_occurrence_id` と、`interval` 引数の値に応じて `visit_start_date` または `visit_end_date`。
