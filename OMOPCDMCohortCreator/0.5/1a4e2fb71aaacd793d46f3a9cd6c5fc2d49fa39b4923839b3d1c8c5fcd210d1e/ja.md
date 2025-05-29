GetPatientEthnicity(ids, conn; tab = person)

与えられた人のIDのリストから、その民族を見つけます。

# 引数:

  * `ids` - `person_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - Personテーブルを表す`SQLTable`; デフォルトは`person`

# 戻り値

  * `df::DataFrame` - `:person_id`と`:ethnicity_concept_id`の列からなる2列の`DataFrame`
