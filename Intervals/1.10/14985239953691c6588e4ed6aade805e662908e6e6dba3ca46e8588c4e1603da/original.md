```
span(interval::AbstractInterval) -> Any
```

The delta between the upper and lower endpoints. For bounded intervals returns a non-negative value while intervals with any unbounded endpoints will throw an `ArgumentError`.

To avoid having to capture the exception use the pattern:

```julia
Intervals.isbounded(interval) ? span(interval) : infinity
```

Where `infinity` is a variable representing the value you wish to use to represent an unbounded, or infinite, span.
