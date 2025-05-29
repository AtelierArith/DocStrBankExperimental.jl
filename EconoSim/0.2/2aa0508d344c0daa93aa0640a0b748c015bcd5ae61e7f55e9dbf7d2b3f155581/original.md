```
Needs - indicates the needs of an Actor.
```

  * usage_priorities::Set{Int64} - the set of usage priorities. If this contains less than 2 elements, usage is randomised.
  * wants_priorities::Set{Int64} -  the set of wants priorities. If this contains less than 2 elements, purchasing wants is randomised.
  * use::Dict{Tuple{Int64, Blueprint}, Marginality} - indicates what the actor will use each cycle. The Int64 in the key tuple indicates priority.
  * wants::Dict{Tuple{Int64, Blueprint}, Marginality} - indicates what the actor will try to purchase each cycle.
