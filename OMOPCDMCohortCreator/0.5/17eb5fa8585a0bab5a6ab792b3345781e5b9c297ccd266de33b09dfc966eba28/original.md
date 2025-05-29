GenerateGroupCounts(data::DataFrame)

Given data in a DataFrame, get group counts based on each feature found in the DataFrame and removes `person_id` for privacy aggregation purposes.

# Arguments:

  * `data::DataFrame` - a DataFrame that must have at least a `person_id` column

# Returns:

  * `df::DataFrame` - a DataFrame that contains the group counts based on each feature found in `data` with the `person_id` field removed for privacy
