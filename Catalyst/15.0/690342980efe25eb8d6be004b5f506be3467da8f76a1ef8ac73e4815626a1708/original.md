```
SymbolicUtils.hasmetadata(reaction::Reaction, md_key::Symbol)
```

Checks if a `Reaction` have a certain metadata field. If it does, returns `true` (else returns `false`).

Arguments:

  * `reaction`: The reaction for which we wish to check if a specific metadata field exist.
  * `md_key`: The metadata for which we wish to check existence of.

Example:

```julia
reaction = @reaction k, 0 --> X, [description="Production reaction"]
hasmetadata(reaction, :description)
```
