```
struct TruncateFilter <: AbstractRadSigFilter{LinearFiltering}
```

Filter that truncates the input signal.

Constructors:

  * `TruncateFilter(; fields...)`

Fields:

  * `interval::IntervalSets.ClosedInterval{<:Union{Real, Unitful.AbstractQuantity{<:Real}}}`: interval to keep
