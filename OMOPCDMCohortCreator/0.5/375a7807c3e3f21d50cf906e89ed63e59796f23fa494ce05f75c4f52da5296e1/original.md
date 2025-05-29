GetVisitProcedure(visit*ids; tab = procedure*occurrence)

Produces SQL statement that, given a list of `visit_id`'s, finds the procedures associated with that visit.

# Arguments:

  * `visit_ids` - list of `visit_id`'s; each ID must be of subtype `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Procedure Occurrence table; default `procedure_occurrence`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:visit_occurrence_id` and `:procedure_concept_id`
