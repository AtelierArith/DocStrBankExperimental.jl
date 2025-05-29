GetVisitConcept(visit*ids; tab = visit*occurrence)

与えられた訪問IDのリストに基づいて、対応するvisit*concept*idを見つけるSQL文を生成します。

# 引数:

  * `visit_ids` - `visit_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません

# キーワード引数:

  * `tab` - Condition Occurrenceテーブルを表す`SQLTable`; デフォルトは`visit_occurrence`

# 戻り値

  * `sql::String` - `String`としての準備されたSQL文
