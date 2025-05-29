GetVisitDate(visit*occurrence*id; interval::Symbol = :start, tab = visit_occurrence)

This function queries a database for the start or end date of the visit occurrence associated with the given `visit_occurrence_id` or list of `visit_occurrence_id`'s.

# Arguments:

  * `visit_occurrence_id`: A single `visit_occurrence_id` or a vector of `visit_occurrence_id`'s to query for.
  * `conn` - database connection using DBInterface

# Keyword Arguments

  * `interval`: A keyword argument that determines whether to query for the visit start date (`interval=:start`) or the visit end date (`interval=:end`). Default value is `interval=:start`.

# Returns:

A dataframe with two columns: `visit_occurrence_id` and either `visit_start_date` or `visit_end_date`, depending on the value of the `interval` argument.
