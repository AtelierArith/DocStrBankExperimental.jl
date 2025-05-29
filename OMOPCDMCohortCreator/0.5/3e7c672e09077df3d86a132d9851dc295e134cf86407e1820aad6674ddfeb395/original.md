GetDatabasePersonIDs(conn; tab = person)

Get all unique `person_id`'s from a database.

# Arguments:

  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Person table; default `person`

# Returns

  * `ids::Vector{Int64}` - the list of persons
