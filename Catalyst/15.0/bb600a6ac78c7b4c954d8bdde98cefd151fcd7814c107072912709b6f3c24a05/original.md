getmisc(reaction::Reaction)

Returns `misc` metadata field for the input reaction.

Arguments:

  * `reaction`: The reaction we wish to retrieve the `misc` metadata field.

Example:

```julia
reaction = @reaction k, 0 --> X, [misc="A reaction"]
getmisc(reaction)
```

Notes:

  * The `misc` field can contain any valid Julia structure. This mean that Catalyst cannot check it

for symbolic variables that are added here. This means that symbolic variables (e.g. parameters of species) that are stored here are not accessible to Catalyst. This can cause troubles when e.g. creating a `ReactionSystem` programmatically (in which case any symbolic variables stored in the `misc` metadata field should also be explicitly provided to the `ReactionSystem` constructor).
