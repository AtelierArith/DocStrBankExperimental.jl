GetPatientGender(ids; tab = person)

指定された `person_id` のリストに対して `gender_concept_id` を取得する SQL 文を返します。

# 引数:

  * `ids` - `person_id` のリスト; 各 ID は `Integer` のサブタイプでなければなりません。

# キーワード引数:

  * `tab` - Person テーブルを表す `SQLTable`; デフォルトは `person`

# 戻り値

  * `df::DataFrame` - `:person_id` と `:gender_concept_id` の列からなる二列の `DataFrame`
