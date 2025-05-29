```
readDegenGeom(filename::String; verbose::Bool=false)
```

Read DegenGeom CSV file written out by OpenVSP to obtain geometry and components.

**Arguments**

  * `filename::String`: DegenGeom filename
  * `verbose::Bool`: Set to `true` to print status messages during file read operation

**Returns**

  * `comp`: Vector of [`VSPComponent`](@ref) objects
