```
getage(tree::ChronoTree; 
	average=mean_, getrelerr::Bool=false, reltol=1e-6) :: Float64
```

Return an average age (from the root node) of tip nodes of the tree. 

The argument `average` defines the method for summarizing the ages to one; by  default it is set to `mean_`.

The argument `getrelerr` controls whether the relative standard deviation is  appended to the output (`(mean, relstd)`) or not (only `mean`); by default it  is set to `false`.

The argument `reltol` is a tolerance of relative error. By default it is set  to `1e-6`. To suppress the judgment, set `reltol=NaN`.
