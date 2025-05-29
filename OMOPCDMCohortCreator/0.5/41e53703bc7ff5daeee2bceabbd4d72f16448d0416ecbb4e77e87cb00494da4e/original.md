function GetCohortSubjectStartDate(df:DataFrame, conn; tab = cohort)

Given a `DataFrame` with a `:cohort_definition_id` column and `:subject_id` column, return the `DataFrame` with an associated `:cohort_start_date` corresponding to a cohort's subject ID in the `DataFrame`

Multiple dispatch that accepts all other arguments like in `GetCohortSubjectStartDate(ids, conn; tab = cohort)`
