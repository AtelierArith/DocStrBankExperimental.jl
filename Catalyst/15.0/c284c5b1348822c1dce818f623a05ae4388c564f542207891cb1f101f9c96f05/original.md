getdescription(reaction::Reaction)

Returns `description` metadata field for the input reaction.

Arguments:

  * `reaction`: The reaction we wish to retrieve the `description` metadata field.

Example:

```julia
reaction = @reaction k, 0 --> X, [description="A reaction"]
getdescription(reaction)
```
