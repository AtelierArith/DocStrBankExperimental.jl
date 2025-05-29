```
struct FunctionModel{O} <: LeafModel{O}
    f::FunctionWrapper{O}
    info::NamedTuple
end
```

A `FunctionModel` is a `LeafModel` that applies a native Julia `Function` in order to compute the outcome.

!!! warning
    Over efficiency concerns, it is mandatory to make explicit the output type `O` by wrapping the `Function` into an object of type `FunctionWrapper{O}` (see [FunctionWrappers](https://github.com/yuyichao/FunctionWrappers.jl).


See also [`LeafModel`](@ref).
