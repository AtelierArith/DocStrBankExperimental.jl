GetMostRecentConditions(ids; tab = condition_occurrence)

Produces SQL statement that, given a list of person IDs, finds their last recorded conditions.

# Arguments:

  * `ids` - list of `person_id`'s; each ID must be of subtype `Integer`

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Condition Occurrence table; default `condition_occurrence`

# Returns

  * `df::DataFrame` - a two column `DataFrame` comprised of columns: `:person_id` and `:condition_concept_id`
