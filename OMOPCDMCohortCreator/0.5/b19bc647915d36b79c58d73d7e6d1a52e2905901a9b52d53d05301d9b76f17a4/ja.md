GetCohortSubjects(cohort_ids, conn; tab = cohort)

与えられたコホートIDのリストに対して、それに対応する被験者を見つけます。

# 引数:

  * `cohort_ids` - `cohort_id`のリスト; 各IDは`Float64`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - `cohort`テーブルを表す`SQLTable`; デフォルトは`cohort`

# 戻り値

  * `df::DataFrame` - `:cohort_definition_id`と`:subject_id`の列からなる2列の`DataFrame`
