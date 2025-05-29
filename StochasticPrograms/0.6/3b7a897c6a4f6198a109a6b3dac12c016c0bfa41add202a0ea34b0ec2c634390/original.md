```
constraint_by_name(stochasticprogram::StochasticProgram,
                   stage::Integer,
                   name::String)::Union{SPConstraintRef, Nothing}
```

Returns the reference of the constraint with name attribute `name` at `stage` of `stochasticprogram` or `Nothing` if no constraint has this name attribute. Throws an error if several constraints have `name` as their name attribute.

```
constraint_by_name(stochasticprogram::StochasticProgram,
                   stage::Integer,
                   name::String,
                   F::Type{<:Union{AbstractJuMPScalar,
                                   Vector{<:AbstractJuMPScalar},
                                   MOI.AbstactFunction}},
                   S::Type{<:MOI.AbstractSet})::Union{SPConstraintRef, Nothing}
```

Similar to the method above, except that it throws an error if the constraint is not an `F`-in-`S` contraint where `F` is either the JuMP or MOI type of the function, and `S` is the MOI type of the set.
