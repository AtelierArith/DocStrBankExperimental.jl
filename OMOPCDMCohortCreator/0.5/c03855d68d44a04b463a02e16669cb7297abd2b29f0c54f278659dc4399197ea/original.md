GetCohortSubjects(cohort_ids; tab = cohort)

Produces SQL statement that, given a list of `cohort_id`'s, finds the subjects associated with that cohort.

# Arguments:

  * `cohort_ids` - list of `cohort_id`'s; each ID must be of subtype `Float64`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the `cohort` table; default `cohort`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:cohort_definition_id` and `:subject_id`
