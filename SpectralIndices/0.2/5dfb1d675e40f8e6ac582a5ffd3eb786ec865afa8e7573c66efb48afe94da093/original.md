```
linear(a::Number, b::Number)
linear(a::AbstractArray, b::AbstractArray)
linear(params::Dict{String, T})
linear(params::DataFrame)
linear(params::YAXArray)
```

Compute the linear kernel `a * b`. This function supports various input types, including numbers, arrays, dictionaries, data frames, and YAXArrays.

# Arguments

  * `a`: First parameter for the linear kernel. Can be a number or an array.
  * `b`: Second parameter for the linear kernel. Can be a number or an array.
  * `params`: A dictionary, data frame, or YAXArray containing the parameters "a" and "b".

# Returns

  * The result of `a * b`. The output type depends on the input types:

      * If `a` and `b` are numbers, the result is a number.
      * If `a` and `b` are arrays, the result is an array with element-wise multiplication.
      * If `params` is used, the result is in the same format as `params` (either a dictionary, DataFrame, or YAXArray).

# Examples

```julia
# Using numbers
result = linear(2, 3)

# Using arrays
result = linear([1, 2, 3], [4, 5, 6])

# Using a dictionary
result = linear(Dict("a" => 2, "b" => 3))

# Using a DataFrame
df = DataFrame(; a=[1, 2, 3], b=[4, 5, 6])
result = linear(df)
```
