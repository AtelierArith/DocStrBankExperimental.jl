GetVisitCondition(visit*ids, conn; tab = visit*occurrence)

与えられた訪問IDのリストに対して、それに対応する条件を見つけます。

# 引数:

  * `visit_ids` - `visit_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - Condition Occurrenceテーブルを表す`SQLTable`; デフォルトは`condition_occurrence`

# 戻り値

  * `df::DataFrame` - `:visit_occurrence_id`と`:condition_concept_id`の列からなる2列の`DataFrame`
