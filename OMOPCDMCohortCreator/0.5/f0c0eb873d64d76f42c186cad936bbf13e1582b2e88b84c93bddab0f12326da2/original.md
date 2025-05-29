GetPatientVisits(ids; tab = visit_occurrence)

Return SQL statement that returns all `visit_occurrence_id` for a given patient list

# Arguments:

  * `ids` - list of `person_id`'s; each ID must be of subtype `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Visit Occurrence table; default `visit_occurrence`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:person_id` and `:visit_occurrence_id`
