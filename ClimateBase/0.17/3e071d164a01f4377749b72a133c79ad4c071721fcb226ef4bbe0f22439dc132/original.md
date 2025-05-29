```
yearlyagg(A::ClimArray, f = mean) -> B
```

Create a new array where the temporal information has been aggregated into years using the function `f`. By convention, the dates of the new array always have month and day number of `1`.
