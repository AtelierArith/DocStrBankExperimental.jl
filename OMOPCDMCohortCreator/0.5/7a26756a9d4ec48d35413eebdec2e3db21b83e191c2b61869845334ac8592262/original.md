GetVisitConcept(visit*ids, conn; tab = visit*occurrence)

Given a list of visit IDs, find their corresponding visit*concept*id's.

# Arguments:

  * `visit_ids` - list of `visit_id`'s; each ID must be of subtype `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Condition Occurrence table; default `visit_occurrence`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:visit_occurrence_id` and `:visit_concept_id`
