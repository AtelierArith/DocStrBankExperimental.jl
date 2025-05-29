GetVisitPlaceOfService(visit*ids, conn; tab = visit*occurrence, join*tab = care*site)

与えられた訪問IDのリストから、サービスの場所を見つけます。

# 引数:

  * `visit_ids` - `visit_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - Condition Occurrenceテーブルを表す`SQLTable`; デフォルトは`visit_occurrence`
  * `join_tab` - Personテーブルを表す`SQLTable`; デフォルトは`care_site`

# 戻り値

  * `df::DataFrame` - `:visit_occurrence_id`と`:condition_concept_id`の列からなる2列の`DataFrame`
