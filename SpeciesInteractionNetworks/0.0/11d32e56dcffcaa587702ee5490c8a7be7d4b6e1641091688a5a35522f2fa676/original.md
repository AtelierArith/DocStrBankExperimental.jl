```
BetaDivComponent
```

The [`betadiversity`](@ref) methods all use a subtype of `BetaDivComponent` as their first argument, to determine which component should be measured.

All of the partitions follow the [Koleff2003Measuring](@citet) approach, where the beta diversity is measured on the cardinality of sets. Specifically, all [`betadiversity`](@ref) functions will return a named tuple with three fields, called `shared`, `left`, and `right`. These represent, respectively, the number of items common to both networks, the number of items unique to the first argument, and the number of items unique to the second argument.

###### References

[Koleff2003Measuring](@citet*)
