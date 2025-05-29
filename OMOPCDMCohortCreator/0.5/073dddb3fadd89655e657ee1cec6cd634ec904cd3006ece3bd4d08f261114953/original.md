GetPatientState(ids; tab = location, join_tab = person)

Return SQL statement where if given a list of person IDs, find their home state.

# Arguments:

  * `ids` - list of `person_id`'s; each ID must be of subtype `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Location table; default `location`
  * `join_tab` - the `SQLTable` representing the Person table; default `person`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:person_id` and `:state`
