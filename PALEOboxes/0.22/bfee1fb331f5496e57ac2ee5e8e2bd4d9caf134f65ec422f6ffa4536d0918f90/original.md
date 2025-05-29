```
create_dispatch_methodlists(model::Model, modeldata::AbstractModelData, arrays_idx::Int, cellranges; kwargs) 
    -> DispatchMethodLists(list_initialize, list_do)
```

Compile lists of `initialize` and `do` methods + corresponding `cellrange` for main loop [`do_deriv`](@ref).

Subset of methods and cellrange to operate on are generated from supplied `cellranges`.

# Keyword arguments

  * `verbose=false`: true for additional log output
  * `generated_dispatch=true`: `true` to create `ReactionMethodDispatchList`s (fast dispatch using generated code, slow compile time),  `false` to create `ReactionMethodDispatchListNoGen` (slow dynamic dispatch, fast compile time)
