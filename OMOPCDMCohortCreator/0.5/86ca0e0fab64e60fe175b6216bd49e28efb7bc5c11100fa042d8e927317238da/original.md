GetMostRecentVisit(ids, conn; tab = visit_occurrence)

Given a list of person IDs, find their last recorded visit.

# Arguments:

  * `ids` - list of `person_id`'s; each ID must be of subtype `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Visit Occurrence table; default `visit_occurrence`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:person_id` and `:visit_occurrence_id`
