GenderFilterPersonIDs(gender*codes; tab = visit*occurrence)

Generates a SQL statement that, given a list of visit concept IDs, `gender_codes` return from the database individuals having at least one entry in the Person table matching at least one of the provided gender types.

# Arguments:

  * `visit_codes` - a vector of `gender_concept_id`'s; must be a subtype of `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Person table; default `person`

# Returns

  * `sql::String` - the SQL representation that runs this filter
