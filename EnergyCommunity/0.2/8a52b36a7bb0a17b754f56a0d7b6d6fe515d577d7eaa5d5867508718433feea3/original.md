```
prepare_summary(::AbstractGroupNC, ECModel::AbstractEC, file_summary_path::AbstractString;
    user_set::Vector=Vector())
```

Prepare the dataframe lists to be saved in an excel file

## Outputs

output_list: Vector{Pair{String, DataFrame}}     Vector of pairs representing the sheets of the Excel file and the corresponding data to save
