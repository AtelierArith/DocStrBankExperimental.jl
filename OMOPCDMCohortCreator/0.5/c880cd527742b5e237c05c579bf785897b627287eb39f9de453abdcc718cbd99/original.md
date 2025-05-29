GetDatabaseCohorts(conn; tab=cohort)

Given a `DataFrame` returns all unique cohort*definition*id associated with a database.

#Arguments:

  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Cohort table; default `cohort`

# Returns

  * `df::DataFrame` - a one column `DataFrame` comprised of columns: `:cohort_definition_id`
