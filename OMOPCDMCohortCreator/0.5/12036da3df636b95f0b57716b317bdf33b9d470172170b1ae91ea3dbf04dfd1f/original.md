StateFilterPersonIDs(states, conn; tab = location, join_tab = person)

Given a list of states, `states`, return from the database individuals found in the provided state list.

# Arguments:

  * `states` - a vector of state abbreviations; must be a subtype of `AbstractString`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Location table; default `location`
  * `join_tab` - the `SQLTable` representing the Person table; default `person`

# Returns

  * `ids::Vector{Int64}` - the list of persons resulting from the filter
