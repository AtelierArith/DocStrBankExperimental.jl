```
arc(place::Place, transition::Transition, type::Symbol)
```

Creates an object of type Arc that joins a place to a transition in a Petri net. Note: acceptable arcs are one of the following:     :in, :read, :inout, :out, :out_many

# Examples

```julia-repl
julia> p1 = place("place1", "input_place")
Place "place1" created.


julia> t1 = transition("transition1")
Transition "transition1" created.


julia> arc(p1, t1, :in)
An arc of type "in", connecting the place: place1 to the transition: transition1.

```

See also [`place`](@ref), [`transition`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref).
