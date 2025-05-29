```
LocalFilters.Window{N}
```

is the union of types of arguments suitable to define a `N`-dimensional *sliding window* that is a `N`-dimensional array of Booleans indicating whether a position belongs to the window of not. Any argument `B` of this type can be converted into a `N`-dimensional array of Booleans by [`kernel(Dims{N}, B)`](@ref LocalFilters.kernel).
