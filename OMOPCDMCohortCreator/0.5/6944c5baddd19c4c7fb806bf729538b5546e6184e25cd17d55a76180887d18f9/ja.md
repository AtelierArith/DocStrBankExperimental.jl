GetVisitPlaceOfService(visit*ids; tab = visit*occurrence, join*tab = care*site)

与えられた訪問IDのリストに基づいて、サービスの場所を見つけるSQL文を生成します。

# 引数:

  * `visit_ids` - `visit_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません

# キーワード引数:

  * `tab` - Condition Occurrenceテーブルを表す`SQLTable`; デフォルトは`visit_occurrence`
  * `join_tab` - Personテーブルを表す`SQLTable`; デフォルトは`care_site`

# 戻り値

  * `sql::String` - `String`としての準備されたSQL文
