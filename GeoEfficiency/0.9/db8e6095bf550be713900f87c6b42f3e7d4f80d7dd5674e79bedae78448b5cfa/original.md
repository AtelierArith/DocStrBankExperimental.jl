```
max_batch(n::Real)
```

set the value of `_max_batch` which give a hint to the program on maxumam number of entries per  detector displayed on the `console` in btach mode. This function `do not` affect the saving of the batch calculation. 

!!! note
    Negative value will display prevent batch results from printed to the `console`.  while `Inf` will print all  batch results to the `console`.


**see also: [`max_batch()`](@ref)**
