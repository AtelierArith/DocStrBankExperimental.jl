GetCohortSubjects(cohort_ids; tab = cohort)

与えられた `cohort_id` のリストに基づいて、そのコホートに関連する被験者を見つける SQL ステートメントを生成します。

# 引数:

  * `cohort_ids` - `cohort_id` のリスト; 各 ID は `Float64` のサブタイプでなければなりません

# キーワード引数:

  * `tab` - `cohort` テーブルを表す `SQLTable`; デフォルトは `cohort`

# 戻り値

  * `df::DataFrame` - `:cohort_definition_id` と `:subject_id` の列からなる二列の `DataFrame`
