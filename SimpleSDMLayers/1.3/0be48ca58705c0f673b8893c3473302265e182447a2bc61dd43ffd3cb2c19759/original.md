```
reclassify(L::SDMLayer, rules::Pair...)
```

Returns a layer where the cells are updated as a function of rules, given as `(function) => value`, where the function must return a `Bool` value. For example, `reclassify(layer, (x -> abs(x)<=1)=>true)` will set a value of `true` to all cells with values in -1;1, and maks all other cells. You can use multiple rules, in which case they are applied sequentially (a later rule can overwrite an earlier one).
