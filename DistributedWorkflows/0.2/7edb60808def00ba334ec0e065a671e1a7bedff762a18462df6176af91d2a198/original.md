```
connect(pnet::Workflow_PetriNet, place::Place, transition::Transition, arc_type::Symbol)
connect(pnet::Workflow_PetriNet, transition::Transition, place::Place, arc_type::Symbol)
```

Given a Petri net connects the place to the transition with the given arc type. 

# Examples

```julia-repl
# initiating an empty Petri net.
julia> pn = Workflow_PetriNet("hello_julia")
A Petri net with name "hello_julia", having 0 ports, 0 places, and 0 transitions.


julia> p1 = place("input1", :string)
Place "input1" created.


julia> p2 = place("input2",:string)
Place "input2" created.


julia> p3 = place("output",:string)
Place "output" created.


julia> t = transition("transition1")
Transition "transition1" created.


julia> connect(pn, p1,t, :in)
A Petri net with name "hello_julia", having 0 ports, 1 places, and 1 transitions.


julia> connect(pn, p2,t, :read)
A Petri net with name "hello_julia", having 0 ports, 2 places, and 1 transitions.


julia> connect(pn, p3,t, :out_many)
A Petri net with name "hello_julia", having 0 ports, 3 places, and 1 transitions.


julia> connect(pn, p1, :in)
A Petri net with name "hello_julia", having 1 ports, 3 places, and 1 transitions.


julia> connect(pn, :in, p2)
A Petri net with name "hello_julia", having 2 ports, 3 places, and 1 transitions.


julia> connect(pn, :out, p3)
A Petri net with name "hello_julia", having 3 ports, 3 places, and 1 transitions.

```

See also [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`remove`](@ref).
