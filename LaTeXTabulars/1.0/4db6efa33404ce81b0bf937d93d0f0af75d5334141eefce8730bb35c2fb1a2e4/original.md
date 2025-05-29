```julia
SimpleCellFormatter(; inf, minus_inf, NaN, nothing, missing)

```

A simple formatter that replaces some commonly used values used in displaying data.

Each field below should contain a string or a `LaTeX` code (otherwise, it is emitted as an escaped string).
