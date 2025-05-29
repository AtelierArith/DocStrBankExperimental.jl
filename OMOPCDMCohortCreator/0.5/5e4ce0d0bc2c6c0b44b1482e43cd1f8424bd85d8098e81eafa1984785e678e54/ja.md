GetVisitCondition(visit*ids; tab = visit*occurrence)

与えられた `visit_id` のリストに基づいて、その訪問に関連する診断された条件を見つける SQL ステートメントを生成します。

# 引数:

  * `visit_ids` - `visit_id` のリスト; 各 ID は `Integer` のサブタイプでなければなりません

# キーワード引数:

  * `tab` - Condition Occurrence テーブルを表す `SQLTable`; デフォルトは `condition_occurrence`

# 戻り値

  * `df::DataFrame` - `:visit_occurrence_id` と `:condition_concept_id` の列からなる二列の `DataFrame`
