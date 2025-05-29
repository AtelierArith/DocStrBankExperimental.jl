```
ProducerBlueprint
```

  * type_id::UUID - the type id of the blueprint.
  * name::String - blueprint name.
  * lifecycle::Restorable - blueprint lifecycle
  * batch_res::Dict{<:Blueprint,Int64} - the necessary resources for a production batch. These are destroyed during production.
  * batch_tools::Dict{<:Blueprint,Int64} - the necessary tools for a production batch. These are used during production.
  * batch::Dict{<:Blueprint,Int64} - output per batch.
