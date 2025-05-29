```
@enum LinearDependence INDEPENDENT TRIVIAL DEPENDENT
```

Linear dependence of the element of a basis representing the indices of the rows of a [`MacaulayNullspace`]. `DEPENDENT` indicates that it is linearly dependent to rows that appear earlier in the basis. `TRIVIAL` indicates that the element was not in the original basis so it is trivially independent.
