function GetCohortSubjectStartDate(cohort*ids, subject*ids; tab=cohort)

与えられたコホートIDとサブジェクトIDのリストから、それらの開始日を返します。

# 引数:

  * `cohort_ids` - `cohort_id`のリスト; 各IDは`Float64`のサブタイプでなければなりません
  * `subject_id` - `subject_id`のリスト; 各IDは`Float64`のサブタイプでなければなりません
  * `conn` - DBInterfaceを使用したデータベース接続

# キーワード引数:

  * `tab` - `cohort`テーブルを表す`SQLTable`; デフォルトは`cohort`

# 戻り値

  * `df::DataFrame` - `:cohort_definition_id`、`:subject_id`、および`:cohort_start_date`の列からなる3列の`DataFrame`
