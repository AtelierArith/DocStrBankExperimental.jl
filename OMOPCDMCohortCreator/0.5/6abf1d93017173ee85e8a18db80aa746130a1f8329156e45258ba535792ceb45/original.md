ConditionFilterPersonIDs(condition*codes, conn; tab = condition*occurrence)

Given a list of condition concept IDs, `condition_codes`, return from the database individuals having at least one entry in the Condition Occurrence table matching at least one of the provided condition types.

# Arguments:

  * `condition_codes` - a vector of `condition_concept_id`'s; must be a subtype of `Integer`
  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Condition Occurrence table; default `condition_occurrence`

# Returns

  * `ids::Vector{Int64}` - the list of persons resulting from the filter
