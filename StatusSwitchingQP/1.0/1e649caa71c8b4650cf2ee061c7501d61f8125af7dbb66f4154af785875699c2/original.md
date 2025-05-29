```
    struct Event{T<:AbstractFloat}
```

Events that assets go IN/OUT(DN or UP), or inequalities go binded (EO, as equality) or not (OE, original ineq), with fields:

```
        From::Status
        To::Status
        id::Int     #asset ID
        L::T        #L
```
