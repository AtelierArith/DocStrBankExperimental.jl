```
checkcondition(c::AbstractCondition, args...; kwargs...)
```

Check a condition (e.g., on a world of a logiset instance).

This function must be implemented for each subtype of `AbstractCondition`.

# Examples

```julia
# Checking a condition on a logiset created from a DataFrame
using SoleData, DataFrames

# Load the iris dataset
iris_df = DataFrame(load_iris());

# Convert the DataFrame to a logiset
iris_logiset = scalarlogiset(iris_df);

# Create a ScalarCondition
condition = ScalarCondition(:sepal_length, >, 5.0);

# Check the condition on the logiset
@assert checkcondition(condition, iris_logiset, 1) == true
```
