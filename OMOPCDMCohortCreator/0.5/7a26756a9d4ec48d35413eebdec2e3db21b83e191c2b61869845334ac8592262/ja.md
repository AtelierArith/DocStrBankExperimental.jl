GetVisitConcept(visit*ids, conn; tab = visit*occurrence)

与えられた訪問IDのリストから、それに対応するvisit*concept*idを見つけます。

# 引数:

  * `visit_ids` - `visit_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - Condition Occurrenceテーブルを表す`SQLTable`; デフォルトは`visit_occurrence`

# 戻り値

  * `df::DataFrame` - `:visit_occurrence_id`と`:visit_concept_id`の列からなる2列の`DataFrame`
