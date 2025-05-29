```
retrieve(actr::AbstractACTR; request...)
```

Retrieves a chunk given a retrieval request. By default, current time is  computed with `get_time`.

# Arguments

  * `actr::AbstractACTR`: an ACT-R object

# Keywords

  * `request...`: optional keyword arguments representing a retrieval request, e.g. person=:bob

# Example

```julia
using ACTRModels 
chunks = [Chunk(country=:Germany, capitol=:Berlin),
        Chunk(country=:Australia, capitol=:Canberra)]
declarative = Declarative(memory=chunks)
parms = (noise=true, s=0.20)
actr = ACTR(;declarative, parms...)
retrieve(actr; country=:Germany)
```
