GetVisitPlaceOfService(visit*ids, conn; tab = visit*occurrence, join*tab = care*site)

Given a list of visit IDs, find their place of service 

# Arguments:

  * `visit_ids` - list of `visit_id`'s; each ID must be of subtype `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Condition Occurrence table; default `visit_occurrence`
  * `join_tab` - the `SQLTable` representing the Person table; default `care_site`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:visit_occurrence_id` and `:condition_concept_id`
