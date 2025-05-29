GetMostRecentVisit(ids, conn; tab = visit_occurrence)

Produces SQL statement that, given a list of person IDs, finds their last recorded visit.

# Arguments:

  * `ids` - list of `person_id`'s; each ID must be of subtype `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Visit Occurrence table; default `visit_occurrence`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:person_id` and `:visit_occurrence_id`
