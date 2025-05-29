GetPatientEthnicity(ids, conn; tab = person)

Given a list of person IDs, find their ethnicity.

# Arguments:

  * `ids` - list of `person_id`'s; each ID must be of subtype `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Person table; default `person`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:person_id` and `:ethnicity_concept_id`
