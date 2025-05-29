Abstract type for all element-wise operations.

In a string query, this is specified using the `%` operator (e.g., `% Abs`, `% Log base 2`):

`EltwiseOperation` := `%` operation ( parameter value )*

Since each `EltwiseOperation` isa [`QueryOperation`](@ref), you can directly apply it to a query (e.g., `Axis("cell") |> Lookup("age") |> Abs()`). For this there should be other constructor(s) tailored for this usage.

An element-wise operation may be applied to scalar, vector ot matrix data. It will preserve the shape of the data, but changes the value(s), and possibly the data type of the elements. For example, `Abs` will compute the absolute value of each value.

To implement a new such operation, the type is expected to be of the form:

```
struct MyOperation <: EltwiseOperation
    ... optional parameters ...
end
@query_operation MyOperation

MyOperation(operation_name::Token, parameter_values::Dict{String, Token})::MyOperation
```

The constructor should use `parse_parameter` for each of the parameters (for example, using `parse_number_assignment`). In addition you will need to invoke [`@query_operation`](@ref) to register the operation so it can be used in a query, and implement the functions listed below. See the query operations module for details and examples.
