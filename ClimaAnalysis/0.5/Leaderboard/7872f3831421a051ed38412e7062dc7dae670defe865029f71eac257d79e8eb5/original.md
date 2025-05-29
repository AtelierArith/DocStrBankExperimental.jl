```
read_rmses(csv_file::String, short_name::String; units = nothing)
```

Read a CSV file and create a RMSEVariable with the `short_name` of the variable.

The format of the CSV file should have a header consisting of the entry "model_name" (or any other text as it is ignored by the function) and rest of the entries should be the category names. Each row after the header should start with the model name and the root mean squared errors for each category for that model. The entries of the CSV file should be separated by commas.

The parameter `units` can be a dictionary mapping model name to unit or a string. If `units` is a string, then units will be the same across all models. If units is `nothing`, then the unit is missing for each model which is denoted by an empty string.
