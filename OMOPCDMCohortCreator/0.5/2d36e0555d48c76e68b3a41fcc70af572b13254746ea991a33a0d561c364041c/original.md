function GetCohortSubjectEndDate(cohort*ids, subject*ids, conn; tab=cohort)

```
Given a list of cohort IDs and subject IDs return their end dates.

# Arguments:

- `cohort_ids` - list of `cohort_id`'s; each ID must be of subtype `Float64`
    
- `subject_id` - list of `subject_id`'s; each ID must be of subtype `Float64`
    
- `conn` - database connection using DBInterface
    
# Keyword Arguments:
    
- `tab` - the `SQLTable` representing the `cohort` table; default `cohort`
```

# Returns

  * `df::DataFrame` - a three column `DataFrame` comprised of columns: `:cohort_definition_id` , `:subject_id` and `:cohort_end_date`
