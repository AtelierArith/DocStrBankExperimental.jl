```
EventDependencyStruct
```

A struct that holds the event dependency information. It has the following fields:

  * `id::Int:` the id of the event
  * `evCont::Vector{Int}:` the index tracking used for HD & HZ. Also it is used to update q,quantum,recomputeNext when x is modified in an event
  * `evDisc::Vector{Int}:` the index tracking used for HD & HZ.
  * `evContRHS::Vector{Int}:` the index tracking used to update other Qs before executing the event
