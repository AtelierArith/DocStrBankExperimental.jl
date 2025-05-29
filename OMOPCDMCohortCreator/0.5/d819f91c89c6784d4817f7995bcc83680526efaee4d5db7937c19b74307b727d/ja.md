GetMostRecentVisit(ids, conn; tab = visit_occurrence)

指定された人のIDのリストに基づいて、最後に記録された訪問を見つけるSQL文を生成します。

# 引数:

  * `ids` - `person_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません

# キーワード引数:

  * `tab` - 訪問発生テーブルを表す`SQLTable`; デフォルトは`visit_occurrence`

# 戻り値

  * `df::DataFrame` - `:person_id`と`:visit_occurrence_id`の列からなる2列の`DataFrame`
