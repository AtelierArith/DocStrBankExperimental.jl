```
Workflow_PetriNet(workflow_name::String)
```

A struct creating an empty Petri net named: "workflow_name". Throws an error, if workflow name is not provided.

Use the `connect()` function to populate the Petri net, and `remove()` function to remove Petri net components.

# Examples

```julia-repl
julia> pn = Workflow_PetriNet("hello_julia")
A Petri net with name "hello_julia", having 0 ports, 0 places, and 0 transitions.


julia> p1 = place("input1", :string)
Place "input1" created.


julia> p2 = place("input2",:string)
Place "input2" created.


julia> p3 = place("output",:string)
Place "output" created.


julia> t = transition("trans")
Transition trans created.


julia> connect(pn, p1, t, :in)
A Petri net with name "hello_julia", having 0 ports, 1 places, and 1 transitions.


julia> connect(pn, p2, t, :read)
A Petri net with name "hello_julia", having 0 ports, 2 places, and 1 transitions.


julia> connect(pn, p3, t, :out_many)
A Petri net with name "hello_julia", having 0 ports, 3 places, and 1 transitions.


julia> connect(pn, p1, :in)
A Petri net with name "hello_julia", having 1 ports, 3 places, and 1 transitions.


julia> connect(pn, :in, p2)
A Petri net with name "hello_julia", having 2 ports, 3 places, and 1 transitions.


julia> connect(pn, :out, p3)
A Petri net with name "hello_julia", having 3 ports, 3 places, and 1 transitions.

```

See also [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`connect`](@ref), [`remove`](@ref), [`generate_workflow`](@ref), [`compile_workflow`](@ref).
