GetVisitProcedure(visit*ids, conn; tab = procedure*occurrence)

与えられた訪問IDのリストに対して、それに対応する手続きを見つけます。

# 引数:

  * `visit_ids` - `visit_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - Condition Occurrenceテーブルを表す`SQLTable`; デフォルトは`procedure_occurrence`

# 戻り値

  * `df::DataFrame` - `:visit_occurrence_id`と`:procedure_concept_id`の列からなる2列の`DataFrame`
