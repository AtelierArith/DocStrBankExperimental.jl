ConditionFilterPersonIDs(condition*codes; tab = condition*occurrence)

Generates a SQL statement that, given a list of condition concept IDs, `condition_codes`, return from the database individuals having at least one entry in the Condition Occurrence table matching at least one of the provided condition types.

# Arguments:

  * `condition_codes` - a vector of `condition_concept_id`'s; must be a subtype of `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Condition Occurrence table; default `condition_occurrence`

# Returns

  * `sql::String` - the SQL representation that runs this filter
