```
==(::BareInterval, ::Number)
==(::Number, ::BareInterval)
==(::Interval, ::Number)
==(::Number, ::Interval)
```

Test whether an interval is the singleton of a given number. In other words, the result is true if and only if the interval contains only that number.

!!! note
    Comparison between intervals is purposely disallowed. Indeed, equality between non-singleton intervals has distinct properties, notably $x = y$ does not imply $x - y = 0$. See instead [`isequal_interval`](@ref).

