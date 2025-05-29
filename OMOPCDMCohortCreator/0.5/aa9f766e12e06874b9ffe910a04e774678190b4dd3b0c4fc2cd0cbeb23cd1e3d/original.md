GetPatientRace(ids, conn; tab = person)

Given a list of person IDs, find their race.

# Arguments:

  * `ids` - list of `person_id`'s; each ID must be of subtype `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Person table; default `person`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:person_id` and `:race_concept_id`
