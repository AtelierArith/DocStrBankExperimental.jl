```
SymbolicUtils.getmetadata(reaction::Reaction, md_key::Symbol)
```

Retrieves a certain metadata value from a `Reaction`. If the metadata does not exist, throws an error.

Arguments:

  * `reaction`: The reaction for which we wish to retrieve a specific metadata value.
  * `md_key`: The metadata for which we wish to retrieve.

Example:

```julia
reaction = @reaction k, 0 --> X, [description="Production reaction"]
getmetadata(reaction, :description)
```
