```
remove(pnet::Workflow_PetriNet, arc::Arc)
```

Remove the arc from the given Petri net.  

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


julia> a1 = arc(p1,t,:in)
An arc of type "in", connecting the place: input1 to the transition: initial_transition.


julia> pn.arcs
3-element Vector{DistributedWorkflows.Arc}:
 An arc of type "in", connecting the place: input1 to the transition: initial_transition.

 An arc of type "read", connecting the place: input2 to the transition: initial_transition.

 An arc of type "out_many", connecting the place: output_result to the transition: initial_transition.


julia> remove(pn, a1)
A Petri net with name "hello_julia", having 3 ports, 3 places, and 1 transitions.


julia> pn.arcs
2-element Vector{DistributedWorkflows.Arc}:
 An arc of type "read", connecting the place: input2 to the transition: initial_transition.

 An arc of type "out_many", connecting the place: output_result to the transition: initial_transition.


```

See also [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref).
