`tryparse_summary(df::AbstractDataFrame, typetoparse)` returns a "long" dataframe with columns `:variable_name`, `:exception_type` and `:exception_msg`.

# Example

```@example
using DataFrames
df = DataFrame(
    :name => ["John", "Roe", "Mary", "Hello", "World"],
    :salary => [5.372, "1.1", "1", "NaN", "#value"],
    :age => string.([20, 13, 17, 22, 100])
)
summary = tryparse_summary(df, Float64)
combine(groupby(summary, [:variable_name, :exception_type, :exception_msg]), nrow)
```
