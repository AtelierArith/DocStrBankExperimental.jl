StateFilterPersonIDs(states; tab = location, join_tab = person)

Generates a SQL statement that, given a list of states, `states`, return from the database individuals found in the provided state list.

# Arguments:

  * `states` - a vector of state abbreviations; must be a subtype of `AbstractString`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Location table; default `location`
  * `join_tab` - the `SQLTable` representing the Person table; default `person`

# Returns

  * `sql::String` - the SQL representation that runs this filter
