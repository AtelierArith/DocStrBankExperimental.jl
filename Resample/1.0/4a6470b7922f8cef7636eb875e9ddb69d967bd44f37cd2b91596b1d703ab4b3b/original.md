```
smote(rng::AbstractRNG, data, col::Union{Int,AbstractString,Symbol}; ratio::Real=1.0, k::Union{Nothing,Int}=nothing)
smote(data, col::Union{AbstractString,Symbol}; ratio::Real=1.0, k::Union{Nothing,Int}=nothing)
```

This is a helper function to simplify balancing `data`. Return the sample obtained via Synthetic Minority Over-sampling TEchnique (SMOTE) for

  * `data`: Data as a matrix or satisfying the tables interface. For matices, each column denotes a point and for tables each row denotes a point.
  * `col`: A column number or name specifying on which column the oversampling needs to be based.
  * `ratio`:   Here, `ratio` specifies the desired ratio between the element types in `col`.   For example, when column `:class` contains 1200 elements of class 1 and 1400 elements of class 2, then `smote(data, :class; ratio=1.0)` will add 200 elements of class 1.   With a ratio of 0.9, smote will add only 60 elements since class 1 comes first in the data and 1400 * 0.9 = 1260 assuming that class 1 comes first in the data and then class 2.   If class 2 would come first, then the ratio of 0.9 will fail since it would need to remove elements from class 1.
  * `k`: Number of nearest neighbors to consider for each point.

!!! note
    This functionality is currently only implemented for 2 classes.

