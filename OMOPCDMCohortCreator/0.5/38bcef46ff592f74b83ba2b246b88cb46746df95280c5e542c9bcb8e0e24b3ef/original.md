GetDatabaseYearRange(conn; tab = observation_period)

Get the years for which data is available from a database.

# Arguments:

  * `conn` - database connection using DBInterface

# Keyword Arguments:

  * `tab` - the `SQLTable` representing the Observation Period table; default `observation_period`

# Returns

  * `year_range::NamedTuple{(:first_year, :last_year), Tuple{Int64, Int64}}` - a NamedTuple where `first_year` is the first year data from the database was available and `last_year` where the last year data from the database was available
