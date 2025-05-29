function GetCohortSubjectStartDate(df:DataFrame, conn; tab = cohort)

与えられた `DataFrame` に `:cohort_definition_id` 列と `:subject_id` 列がある場合、`DataFrame` 内のコホートのサブジェクトIDに対応する `:cohort_start_date` を持つ `DataFrame` を返します。

`GetCohortSubjectStartDate(ids, conn; tab = cohort)` のように、他のすべての引数を受け入れる多重ディスパッチ。
