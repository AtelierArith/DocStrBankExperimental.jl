```
save_reactionsystem(filename::String, rn::ReactionSystem; annotate = true, safety_check = true)
```

Save a `ReactionSystem` model to a file. The `ReactionSystem` is saved as runnable Julia code. This can both be used to save a `ReactionSystem` model, but also to write it to a file for easy inspection.

Arguments:

  * `filename`: The name of the file to which the `ReactionSystem` is saved.
  * `rn`: The `ReactionSystem` which should be saved to a file.
  * `annotate = true`: Whether annotation should be added to the file.
  * `safety_check = true`: After serialisation, Catalyst will automatically load the serialised `ReactionSystem` and check that it is equal to `rn`. If it is not, an error will be thrown. For models without the `connection_type` field, this should not happen. If performance is required (i.e. when saving a large number of models), this can be disabled by setting `safety_check = false`.

Example:

```julia
rn = @reaction_network begin
    (p,d), 0 <--> X
end
save_reactionsystem("rn.jls", rn)
```

The model can now be loaded using

```julia
rn = include("rn.jls")
```

Notes:

  * `ReactionSystem`s with the `connection_type` field has this ignored (saving of this field has not been implemented yet).
  * `ReactionSystem`s with non-`ReactionSystem` sub-systems (e.g. `ODESystem`s) cannot be saved.
  * Reaction systems with components that have units cannot currently be saved.
  * The `ReactionSystem` is saved using *programmatic* (not DSL) format for model creation.
