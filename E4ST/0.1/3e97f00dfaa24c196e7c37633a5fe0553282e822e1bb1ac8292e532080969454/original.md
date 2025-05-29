```
join_sim_tables(post_mod_data, keep_col)
```

Joins tables for multiple sims stored in `post_mod_data`, with `keep_col` as the column to keep, and the remaining columns as the joining columns.

  * `replace_missing` - replaces missing values in res after the tables are joined with the value of the kw arg. To keep missing values, set replace_missing = missing.
