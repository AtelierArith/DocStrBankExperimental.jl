```
connect(pnet::Workflow_PetriNet, port_type::Symbol, place::Place)
connect(pnet::Workflow_PetriNet, place::Place, port_type::Symbol)
```

Given a Petri net, connects the given place to a port of name port*name and type port*type. 

# Examples

```julia-repl
julia> pn = Workflow_PetriNet("hello_julia")
A Petri net with name "hello_julia", having 0 ports, 0 places, and 0 transitions.


julia> p1 = place("input1", :string)
Place "input1" created.


julia> p2 = place("input2", :string)
Place "input2" created.


julia> p3 = place("output_result", :string)
Place "output_result" created.


julia> t = transition("initial_transition")
Transition "initial_transition" created.


julia> connect(pn,[(p1, :in),(p2, :read),(p3, :out_many)], t)
A Petri net with name "hello_julia", having 0 ports, 3 places, and 1 transitions.

julia> prt = port(:in, p1)
A port of type "in", connected to place "input1".


julia> connect(pn, p1, prt)
A Petri net with name "hello_julia", having 1 ports, 3 places, and 1 transitions.


```

See also [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`remove`](@ref).
