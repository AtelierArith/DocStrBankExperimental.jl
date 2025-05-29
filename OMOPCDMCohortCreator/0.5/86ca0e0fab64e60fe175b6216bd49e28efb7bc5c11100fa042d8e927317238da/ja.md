GetMostRecentVisit(ids, conn; tab = visit_occurrence)

与えられた人のIDのリストから、最後に記録された訪問を見つけます。

# 引数:

  * `ids` - `person_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - 訪問発生テーブルを表す`SQLTable`; デフォルトは`visit_occurrence`

# 戻り値

  * `df::DataFrame` - `:person_id`と`:visit_occurrence_id`の列からなる2列の`DataFrame`
