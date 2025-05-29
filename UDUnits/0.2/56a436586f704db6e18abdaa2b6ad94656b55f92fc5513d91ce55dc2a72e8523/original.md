```
system = System()
```

Load the default SI unit system. `system` behaves similar to a dictionary as it supports indexing and the function `haskey` (to determine if a unit is a valid):

```julia
using UDUnits
sys = System()
m = sys["meter"]
haskey(sys,"μm") # returns true
```
