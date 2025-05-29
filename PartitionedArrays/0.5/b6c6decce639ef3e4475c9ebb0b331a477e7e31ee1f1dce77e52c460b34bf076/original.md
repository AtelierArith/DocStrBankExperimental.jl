```
OwnAndGhostIndices
```

Container for local indices stored as own and ghost indices separately. Local indices are defined by concatenating own and ghost ones.

# Properties

  * `own::OwnIndices`: Container for the own indices.
  * `ghost::GhostIndices`: Container for the ghost indices.
  * `global_to_owner`: [optional: it can be `nothing`] Vector containing the owner of each global id.

# Supertype hierarchy

```
OwnAndGhostIndices{A} <: AbstractLocalIndices
```

where `A=typeof(global_to_owner)`.
