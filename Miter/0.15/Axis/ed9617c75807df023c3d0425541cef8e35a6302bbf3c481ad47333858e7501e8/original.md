```julia
bounds_xy(a)

```

Return two intervals for the axis bounds of the plot contents.

# Extending

User defined types `T` can either define a `bounds_xy(::Tuple{T,T})` method (or other applicable combinations), or a method for `extrema(::T)`.
