```
remove(pnet::Workflow_PetriNet,  transition::Transition)
```

Remove the transition from the given Petri net.  

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


julia> pn.transitions
1-element Vector{DistributedWorkflows.Transition}:
 Transition "initial_transition" created.


julia> remove(pn, t)
A Petri net with name "hello_julia", having 2 ports, 2 places, and 0 transitions.


julia> pn.transitions
DistributedWorkflows.Transition[]


```

See also [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref).
