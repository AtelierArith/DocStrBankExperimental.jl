function GetCohortSubjectEndDate(df:DataFrame, conn; tab = cohort)

Given a `DataFrame` with a `:cohort_definition_id` column and `:subject_id` column, return the `DataFrame` with an associated `:cohort_end_date` corresponding to a given `cohort_definition_id` and `subject_id` in the `DataFrame`

Multiple dispatch that accepts all other arguments like in `GetCohortSubjectEndDate(ids, conn; tab = cohort)`
