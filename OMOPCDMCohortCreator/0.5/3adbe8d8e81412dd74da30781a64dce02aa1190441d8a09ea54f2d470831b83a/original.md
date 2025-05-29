RaceFilterPersonIDs(race_codes; tab = person)

Generates a SQL statement that, given a list of `race_concept_id`'s, return from the database individuals having at least one entry in the Person table matching at least one of the provided race types.

# Arguments:

  * `race_codes` - a vector of `race_concept_id`'s; must be a subtype of `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Person table; default `person`

# Returns

  * `sql::String` - the SQL representation that runs this filter
