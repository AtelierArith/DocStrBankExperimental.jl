```
sectors(C::Commodity)
```

Return only the sectors that have the input commodity in their production block. 

This is an optimization in building the model as the structure is very sparse  iterating over all sectors is expensive.
