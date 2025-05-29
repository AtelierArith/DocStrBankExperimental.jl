```
defVars(dimNames, dimTypes; <keyword arguments>)
```

Define empty NDSparse IndexedTable(s) with the specific dimension(s) and type.

# Arguments

  * `dimNames`: Array of names of the dimensions to define
  * `dimTypes`: Array of types of the dimensions
  * `valueType` (def: `Float64`):  Type of the value column of the table
  * `n` (def=`1`): Number of copies of the specified tables to return (useful to define multiple variables at once. In such cases a tuple is returned)

# # Examples

# ```julia

# julia> price,demand,supply = defVars(["region","item","class"],[String,String,Int64],valueType=Float64,n=3 )

# julia> waterContent = defVars(["region","item"],[String,String])

# julia> price["US","apple",1] = 3.2

# julia> waterContent["US","apple"] = 0.2

# ```

# 
