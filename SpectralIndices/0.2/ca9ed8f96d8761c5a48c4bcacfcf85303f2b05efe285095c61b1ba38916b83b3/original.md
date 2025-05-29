```
poly(a::T, b::T, c::T, p::T) where T <: Number
poly(a::T, b::T, c::T, p::T) where T <: AbstractArray
poly(params::Dict{String, T})
poly(params::DataFrame)
poly(params::YAXArray)
```

Compute the polynomial kernel `(a * b + c) ^ p`. This function supports various input types, including numbers, arrays, dictionaries, data frames, and YAXArrays.

# Arguments

  * `a`: First parameter for the polynomial kernel. Can be a number or an array.
  * `b`: Second parameter for the polynomial kernel. Can be a number or an array.
  * `c`: Coefficient added to the product of `a` and `b`. Can be a number or an array.
  * `p`: Exponent to which the sum of the product and coefficient is raised. Can be a number or an array.
  * `params`: A dictionary, data frame, or YAXArray containing the parameters "a", "b", "c", and "p".

# Returns

  * The result of `(a * b + c) ^ p`. The output type depends on the input types:

      * If `a`, `b`, `c`, and `p` are numbers, the result is a number.
      * If `a`, `b`, `c`, and `p` are arrays, the result is an array with the operation applied element-wise.
      * If `params` is used, the result matches the format of `params` (either a dictionary, DataFrame, or YAXArray).

# Examples

```julia
# Using numbers
result = poly(2, 3, 1, 2)

# Using arrays
result = poly([1, 2, 3], [4, 5, 6], [1, 1, 1], [2, 2, 2])

# Using a dictionary
result = poly(Dict("a" => 2, "b" => 3, "c" => 1, "p" => 2))

# Using a DataFrame
df = DataFrame(; a=[1, 2, 3], b=[4, 5, 6], c=[1, 1, 1], p=[2, 2, 2])
result = poly(df)
```
