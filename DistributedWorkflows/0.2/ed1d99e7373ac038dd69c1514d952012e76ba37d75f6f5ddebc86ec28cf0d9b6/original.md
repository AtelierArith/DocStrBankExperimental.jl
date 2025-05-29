```
transition(name::String, exp::Vector{String})
transition(name::String, exp::Vector{String}, condition::String)
```

Creates an object of type Transition for the Petri net object containing an expression. If a condition string is given, the the transition is a condiational transition.

Note: the condition and/or expression follows Fortran style expression. The following are possible expressions that can be wrapped in a string: Comparison expressions:  :lt: :le: :gt: :ge: :ne: :eq: Boolean expressions:  :or: :and: :not: Operations:  +, -, *, /, :=

See the example on how to use.

# Examples

```julia-repl
julia> transition("transition1")
Transition "transition1" created.

julia> transition("do_stuff", "counter :eq: 0UL")
A conditional transition "do_stuff" created.

```

See also [`place`](@ref), [`arc`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref).
