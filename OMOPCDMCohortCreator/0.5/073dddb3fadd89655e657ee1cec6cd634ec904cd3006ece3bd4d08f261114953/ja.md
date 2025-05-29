GetPatientState(ids; tab = location, join_tab = person)

与えられた人のIDのリストから、彼らのホームステートを見つけるSQL文を返します。

# 引数:

  * `ids` - `person_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - Locationテーブルを表す`SQLTable`; デフォルトは`location`
  * `join_tab` - Personテーブルを表す`SQLTable`; デフォルトは`person`

# 戻り値

  * `df::DataFrame` - `:person_id`と`:state`の列からなる2列の`DataFrame`
