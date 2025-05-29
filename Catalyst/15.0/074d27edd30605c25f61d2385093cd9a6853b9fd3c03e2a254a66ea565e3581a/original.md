hasmisc(reaction::Reaction)

Returns `true` if the input reaction has the `misc` metadata field assigned, else `false`.

Arguments:

  * `reaction`: The reaction we wish to check for the `misc` metadata field.

Example:

```julia
reaction = @reaction k, 0 --> X, [misc="A reaction"]
hasmisc(reaction)
```
