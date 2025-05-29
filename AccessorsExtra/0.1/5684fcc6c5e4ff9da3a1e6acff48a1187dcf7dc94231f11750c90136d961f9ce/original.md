```
concat(optics...)
o1 ++ o2 ++ o3 ++ ...
```

Concatenate multiple optics, producing a new optic that references all values from them.

Specifically, with a concat-optic:

  * `getall` is the concatenation of individual `getall`s
  * `setall` accepts a collection of values that are distributed over individual optics based on their `getall` counts
  * `modify` applies `modify` for each optic in turn, with the same transformation function
