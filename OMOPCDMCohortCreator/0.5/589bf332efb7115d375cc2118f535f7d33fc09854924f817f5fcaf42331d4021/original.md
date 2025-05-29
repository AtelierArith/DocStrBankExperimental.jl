VisitFilterPersonIDs(visit*codes, conn; tab = visit*occurrence)

Given a list of visit concept IDs, `visit_codes` return from the database patients matching at least one of the provided visit codes from the Visit Occurrence table.

# Arguments:

  * `visit_codes` - a vector of `visit_concept_id`'s; must be a subtype of `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Visit Occurrence table; default `visit_occurrence`

# Returns

  * `ids::Vector{Int64}` - the list of persons resulting from the filter
