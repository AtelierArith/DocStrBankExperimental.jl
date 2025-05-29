```
DictDB(x::MecabNGrams)
```

Initialize a dict DB with additional containers and Metadata for MecabNGrams

# Arguments

  * `x`: MecabNGrams object

# Example

```julia
db = DictDB(MecabNGrams(2, " ", Mecab()))
```

# Returns

  * `DictDB`: A DictDB object with additional containers and Metadata for MecabNGrams
