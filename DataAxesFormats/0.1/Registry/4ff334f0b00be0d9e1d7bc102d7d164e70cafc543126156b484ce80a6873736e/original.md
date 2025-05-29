Abstract type for all reduction operations.

In a string query, this is specified using the `%>` operator (e.g., `%> Sum`, `%> Quantile fraction 0.05`):

`ReductionOperation` := `%>` operation ( parameter value )*

Since each `ReductionOperation` isa [`QueryOperation`](@ref), you can directly apply it to a query (e.g., `Axis("cell") |> Axis("gene") |> Lookup("UMIs") |> Quantile(0.05)`). For this there should be other constructor(s) tailored for this usage.

A reduction operation may be applied to matrix or vector data. It will reduce (eliminate) one dimension of the data, and possibly the result will have a different data type than the input. When applied to a vector, the operation will return a scalar. When applied to a matrix, it assumes the matrix is in column-major layout, and will return a vector with one entry per column, containing the result of reducing the column to a scalar.

To implement a new such operation, the type is expected to be of the form:

```
struct MyOperation <: ReductionOperation
    ... optional parameters ...
end

MyOperation(operation_name::Token, parameter_values::Dict{String, Token})::MyOperation
```

The constructor should use `parse_parameter` for each of the parameters (for example, using typically `parse_number_assignment`). In addition you will need to invoke [`@query_operation`](@ref) to register the operation so it can be used in a query, and implement the functions listed below. See the query operations module for details and examples.
