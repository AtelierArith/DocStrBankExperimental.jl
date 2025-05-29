GenderFilterPersonIDs(gender*codes, conn; tab = visit*occurrence)

Given a list of visit concept IDs, `gender_codes` return from the database individuals having at least one entry in the Person table matching at least one of the provided gender types.

# Arguments:

  * `visit_codes` - a vector of `gender_concept_id`'s; must be a subtype of `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Person table; default `person`

# Returns

  * `ids::Vector{Int64}` - the list of persons resulting from the filter
