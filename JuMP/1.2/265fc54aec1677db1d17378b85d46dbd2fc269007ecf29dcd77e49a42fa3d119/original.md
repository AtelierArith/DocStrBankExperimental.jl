```
callback_node_status(cb_data, model::Model)
```

Return an [`MOI.CallbackNodeStatusCode`](@ref) enum, indicating if the current primal solution available from [`callback_value`](@ref) is integer feasible.
