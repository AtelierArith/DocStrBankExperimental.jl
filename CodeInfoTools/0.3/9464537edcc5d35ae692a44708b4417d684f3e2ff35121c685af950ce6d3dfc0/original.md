!!! warning
    It is relatively difficult to prevent the user from shooting themselves in the foot with this sort of functionality. Please be aware of this. Segfaults should be cautiously expected.


```julia
lambda(m::Module, src::Core.CodeInfo)
lambda(m::Module, src::Core.CodeInfo, nargs::Int)
const λ = lambda
```

Create an anonymous `@generated` function from a piece of `src::Core.CodeInfo`. The `src::Core.CodeInfo` is checked for consistency by [`verify`](@ref).

`lambda` has a 2 different forms. The first form, given by signature:

```julia
lambda(m::Module, src::Core.CodeInfo)
```

tries to detect the correct number of arguments automatically. This may fail (for any number of internal reasons). Expecting this, the second form, given by signature:

```julia
lambda(m::Module, src::Core.CodeInfo, nargs::Int)
```

allows the user to specify the number of arguments via `nargs`.

`lambda` also has the shorthand `λ` for those lovers of Unicode.
