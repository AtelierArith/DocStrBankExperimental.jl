GetVisitConcept(visit*ids; tab = visit*occurrence)

Produces SQL statement that, given a list of visit IDs, find their corresponding visit*concept*id's.

# Arguments:

  * `visit_ids` - list of `visit_id`'s; each ID must be of subtype `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Condition Occurrence table; default `visit_occurrence`

# Returns

  * `sql::String` - Prepared SQL statement as a `String`
