```
RBF(a::T, b::T, sigma::T) where T <: Number
RBF(a::T, b::T, sigma::T) where T <: AbstractArray
RBF(params::Dict{String, T})
RBF(params::DataFrame)
RBF(params::YAXArray)
```

Compute the Radial Basis Function (RBF) kernel `exp((-1.0 * (a - b) ^ 2.0) / (2.0 * sigma ^ 2.0))`. This function supports various input types, including numbers, arrays, dictionaries, data frames, and YAXArrays.

# Arguments

  * `a`: First parameter for the RBF kernel. Can be a number or an array.
  * `b`: Second parameter for the RBF kernel. Can be a number or an array.
  * `sigma`: Length-scale parameter for the RBF kernel. Can be a number or an array.
  * `params`: A dictionary, data frame, or YAXArray containing the parameters "a", "b", and "sigma".

# Returns

  * The result of the RBF kernel. The output type depends on the input types:

      * If `a`, `b`, and `sigma` are numbers, the result is a number.
      * If `a`, `b`, and `sigma` are arrays, the result is an array with the operation applied element-wise.
      * If `params` is used, the result matches the format of `params` (either a dictionary, DataFrame, or YAXArray).

# Examples

```julia
# Using numbers
result = RBF(1, 2, 0.5)

# Using arrays
result = RBF([1, 2, 3], [4, 5, 6], [0.5, 0.5, 0.5])

# Using a dictionary
result = RBF(Dict("a" => 1, "b" => 2, "sigma" => 0.5))

# Using a DataFrame
df = DataFrame(; a=[1, 2, 3], b=[4, 5, 6], sigma=[0.5, 0.5, 0.5])
result = RBF(df)
```
