GetCohortSubjects(cohort_ids, conn; tab = cohort)

Given a list of cohort IDs, find their corresponding subjects.

# Arguments:

  * `cohort_ids` - list of `cohort_id`'s; each ID must be of subtype `Float64`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the `cohort` table; default `cohort`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:cohort_definition_id` and `:subject_id`
