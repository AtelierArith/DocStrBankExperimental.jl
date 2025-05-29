hasdescription(reaction::Reaction)

Returns `true` if the input reaction has the `description` metadata field assigned, else `false`.

Arguments:

  * `reaction`: The reaction we wish to check for the `description` metadata field.

Example:

```julia
reaction = @reaction k, 0 --> X, [description="A reaction"]
hasdescription(reaction)
```
