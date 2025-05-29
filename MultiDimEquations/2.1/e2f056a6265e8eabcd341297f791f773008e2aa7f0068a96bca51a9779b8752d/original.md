```
defVars(size; <keyword arguments>)
```

Define multidimensional array(s) with the specific dimension(s) and type filled all with `missing` values.

# Arguments

  * `size`: Tuple of the dimensions required
  * `valueType` (def: `Float64`):  Inner type of the array required
  * `n` (def=`1`): Number of copies of the specified tables to return (useful to define multiple variables at once. In such cases a tuple is returned)
  * `missingValue` (def=`missing`): How to fill the matrix with

# # Examples

# ```julia

# julia> price,demand,supply = defVars((3,4,5),valueType=Float64,n=3 )

# julia> waterContent = defVars((3,4))

# julia> price[2,3,1] = 3.2

# julia> waterContent[2,3] = 0.2

# ```

# 
