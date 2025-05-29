```
function interaction(ops::OperatorProduct; name="", reorder::Union{Function,Nothing}=nothing,
    factor=one(_dtype.factor), weight=zero(_dtype.weight), operator=Sum())
```

Create a Interaction-type FeynmanGraph from given OperatorProduct `ops`, including several quantum operators for a vertex. One can call a reorder function for the operators ordering.  
