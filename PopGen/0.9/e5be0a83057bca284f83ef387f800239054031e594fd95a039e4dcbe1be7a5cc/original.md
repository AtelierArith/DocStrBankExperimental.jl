```
alleleaverage(data::PopData; rounding::Bool = true)
```

Returns a NamedTuple of the average number of alleles ('mean') and standard deviation (`stdev`) of a `PopData`. Use `rounding = false` to not round results. Default (`true`) rounds to 4 digits.
