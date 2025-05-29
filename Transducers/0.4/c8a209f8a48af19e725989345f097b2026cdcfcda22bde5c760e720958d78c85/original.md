```
xf'
```

`xf'(rf₁)` is a shortcut for calling `reducingfunction(xf, rf₁)`.

More precisely, adjoint `xf′` of a transducer `xf` is a *reducing function transform* `rf₁ -> rf₂`.  That is to say, `xf'` a function that maps a reducing function `rf₁` to another reducing function `rf₂`.

# Examples

```jldoctest
julia> using Transducers

julia> y = Map(inv)'(+)(10, 2)
10.5

julia> y == +(10, inv(2))
true
```
