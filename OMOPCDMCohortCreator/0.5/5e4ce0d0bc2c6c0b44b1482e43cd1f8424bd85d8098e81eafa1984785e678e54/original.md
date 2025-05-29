GetVisitCondition(visit*ids; tab = visit*occurrence)

Produces SQL statement that, given a list of `visit_id`'s, finds the conditions diagnosed associated with that visit.

# Arguments:

  * `visit_ids` - list of `visit_id`'s; each ID must be of subtype `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Condition Occurrence table; default `condition_occurrence`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:visit_occurrence_id` and `:condition_concept_id`
