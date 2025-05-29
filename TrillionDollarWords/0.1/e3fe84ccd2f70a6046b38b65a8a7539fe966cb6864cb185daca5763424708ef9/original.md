```
prepare_probe(outcome_data::DataFrame; layer::Int=24, value_var::Symbol=:value)
```

Prepare data for a linear probe. The `outcome_data` should be a `DataFrame` with a `sentence_id` column, which should contain unique values. There should also be a column containing the outcome variable. By default, this column is assumed to be called `value`, but this can be changed with the `value_var` argument. The `layer` argument indicates which layer to use for the probe. The default is the last layer (24).
