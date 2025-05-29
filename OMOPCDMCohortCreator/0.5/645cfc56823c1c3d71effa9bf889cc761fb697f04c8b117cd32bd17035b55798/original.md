GetPatientEthnicity(ids, conn; tab = person)

Return SQL statement that gets the `ethnicity_concept_id` for a given list of `person_id`'s

# Arguments:

  * `ids` - list of `person_id`'s; each ID must be of subtype `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Person table; default `person`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:person_id` and `:ethnicity_concept_id`
