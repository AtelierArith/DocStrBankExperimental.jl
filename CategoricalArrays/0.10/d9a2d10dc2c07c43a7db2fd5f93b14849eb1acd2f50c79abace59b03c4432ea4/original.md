```
categorical(A::AbstractArray; levels=nothing, ordered=false, compress=false)
```

Construct a categorical array with the values from `A`.

The `levels` keyword argument can be a vector specifying possible values for the data (this is equivalent to but more efficient than calling [`levels!`](@ref) on the resulting array). If `levels` is omitted and the element type supports it, levels are sorted in ascending order; else, they are kept in their order of appearance in `A`. The `ordered` keyword argument determines whether the array values can be compared according to the ordering of levels or not (see [`isordered`](@ref)).

If `compress` is `true`, the smallest reference type able to hold the number of unique values in `A` will be used. While this will reduce memory use, passing this parameter will also introduce a type instability which can affect performance inside the function where the call is made. Therefore, use this option with caution (the one-argument version does not suffer from this problem).

```
categorical(A::CategoricalArray; compress=false, levels=nothing, ordered=false)
```

If `A` is already a `CategoricalArray`, its levels, orderedness and reference type are preserved unless explicitly overriden.
