GetMostRecentConditions(ids, conn; tab = condition_occurrence)

与えられた人のIDのリストから、最後に記録された状態を見つけます。

# 引数:

  * `ids` - `person_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - Condition Occurrenceテーブルを表す`SQLTable`; デフォルトは`condition_occurrence`

# 戻り値

  * `df::DataFrame` - `:person_id`と`:condition_concept_id`の列からなる2列の`DataFrame`
