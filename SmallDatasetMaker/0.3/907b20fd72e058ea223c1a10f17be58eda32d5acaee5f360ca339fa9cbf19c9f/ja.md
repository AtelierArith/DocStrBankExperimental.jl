`tryparse_summary(df::AbstractDataFrame, typetoparse)` は、列 `:variable_name`、`:exception_type`、および `:exception_msg` を持つ「ロング」データフレームを返します。

# 例

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
