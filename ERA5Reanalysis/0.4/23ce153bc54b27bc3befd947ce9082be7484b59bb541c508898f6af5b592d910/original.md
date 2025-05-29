```
isSingle(
    ID :: AbstractString;
    throw :: Bool = true,
    dolog :: Bool = false
) -> tf :: Bool
```

Extracts information of the Single-Level Variable with the ID `ID`.  If no Single-Level Variable with this ID exists, an error is thrown.

# Arguments

  * `RegID` : The keyword ID that will be used to identify the Single-Level Variable.       If the ID is not valid (i.e. not being used), then an error will be thrown.
  * `throw` : If `true`, then throws an error if `RegID` is not a valid Single-Level Variable identifier instead of returning the Boolean `tf`
  * `dolog` : If `true`, then return logging to screen along with results

# Returns

  * `tf` : True / False
