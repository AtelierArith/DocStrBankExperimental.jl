function GetCohortSubjectEndDate(df:DataFrame, conn; tab = cohort)

与えられた `DataFrame` に `:cohort_definition_id` 列と `:subject_id` 列がある場合、指定された `cohort_definition_id` と `subject_id` に対応する `:cohort_end_date` を持つ `DataFrame` を返します。

`GetCohortSubjectEndDate(ids, conn; tab = cohort)` のように、他のすべての引数を受け入れる多重ディスパッチ。
