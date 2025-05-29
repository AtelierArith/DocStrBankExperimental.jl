GetVisitPlaceOfService(visit*ids; tab = visit*occurrence, join*tab = care*site)

Produces SQL statement that, given a list of visit IDs, find their place of service 

# Arguments:

  * `visit_ids` - list of `visit_id`'s; each ID must be of subtype `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Condition Occurrence table; default `visit_occurrence`
  * `join_tab` - the `SQLTable` representing the Person table; default `care_site`

# Returns

  * `sql::String` - Prepared SQL statement as a `String`
