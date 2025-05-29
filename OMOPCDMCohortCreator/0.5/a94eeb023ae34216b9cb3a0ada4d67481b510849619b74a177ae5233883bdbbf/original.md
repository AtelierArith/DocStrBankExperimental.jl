RaceFilterPersonIDs(race_codes, conn; tab = person)

Given a list of condition concept IDs, `race_codes`, return from the database individuals having at least one entry in the Person table matching at least one of the provided race types.

# Arguments:

  * `race_codes` - a vector of `race_concept_id`'s; must be a subtype of `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Person table; default `person`

# Returns

  * `ids::Vector{Int64}` - the list of persons resulting from the filter
