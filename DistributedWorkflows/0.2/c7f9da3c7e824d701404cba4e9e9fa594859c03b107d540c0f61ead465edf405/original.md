```
remove(pnet::Workflow_PetriNet, port::Port)
```

Remove the port from the given Petri net.  

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


julia> connect(pn, p1, :in)
A Petri net with name "hello_julia", having 1 ports, 3 places, and 1 transitions.


julia> connect(pn, p2, :in)
A Petri net with name "hello_julia", having 2 ports, 3 places, and 1 transitions.


julia> connect(pn, p3, :out)
A Petri net with name "hello_julia", having 3 ports, 3 places, and 1 transitions.


julia> pn.ports
3-element Vector{DistributedWorkflows.Port}:
 A port of type "in" connected to place "input1".

 A port of type "in" connected to place "input2".

 A port of type "out" connected to place "output_result".


julia> prt = port(:in, p1)
A port of type "in" connected to place "input1".


julia> remove(pn, prt)
A Petri net with name "hello_julia", having 2 ports, 3 places, and 1 transitions.


julia> pn.ports
2-element Vector{DistributedWorkflows.Port}:
 A port of type "in" connected to place "input2".

 A port of type "out" connected to place "output_result".


```

See also [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref).
