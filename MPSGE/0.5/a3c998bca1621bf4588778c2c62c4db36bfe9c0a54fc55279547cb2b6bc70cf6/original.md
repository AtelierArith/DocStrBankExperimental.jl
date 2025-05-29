```
cost_function(S::ScalarSector; virtual = false)
cost_function(S::ScalarSector, nest::Symbol; virtual = false)
```

Return a vector of cost functions for the given sector and nest. If `nest` is  not provided return the cost function for input tree. 

`nest` is the symbol representing the nest. This can also be the name of a  commodity. 

If `virtual` is true, return the virtual cost functions.
