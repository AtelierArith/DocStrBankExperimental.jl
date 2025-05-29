GetMostRecentConditions(ids; tab = condition_occurrence)

指定された人のIDのリストに基づいて、最後に記録された状態を見つけるSQL文を生成します。

# 引数:

  * `ids` - `person_id`のリスト; 各IDは`Integer`のサブタイプでなければなりません

# キーワード引数:

  * `tab` - Condition Occurrenceテーブルを表す`SQLTable`; デフォルトは`condition_occurrence`

# 戻り値

  * `df::DataFrame` - `:person_id`と`:condition_concept_id`の列からなる2列の`DataFrame`
