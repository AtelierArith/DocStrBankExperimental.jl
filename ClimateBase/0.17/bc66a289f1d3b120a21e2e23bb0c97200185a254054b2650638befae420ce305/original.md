```
monthlyagg(A::ClimArray, f = mean; mday = 15) -> B
```

Create a new array where the temporal information has been aggregated into months using the function `f`. The dates of the new array always have day number of `mday`.
