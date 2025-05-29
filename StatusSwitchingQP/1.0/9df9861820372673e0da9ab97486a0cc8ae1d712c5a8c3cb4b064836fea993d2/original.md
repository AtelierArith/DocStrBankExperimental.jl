```
    @enum Status
```

Status: assets go IN/OUT(DN or UP), or inequalities go binded (EO, as equality) or not (OE, original ineq), with fields:

```
        IN  #within the lower and upper bound
        DN  #down, lower bound
        UP  #upper bound
        OE  #original <= not active
        EO  #edge, <= as =
```
