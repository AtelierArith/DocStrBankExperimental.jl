```
generate_workflow(pnet::Workflow_PetriNet)
generate_workflow(pnet::Workflow_PetriNet, path::String)
```

Given a Petri net description, creates an XML workflow and writes it to a file in the path.

# Examples

```julia-repl
julia> pn = Workflow_PetriNet("hello_julia")
A Petri net with name "hello_julia", having 0 ports, 0 places, and 0 transitions.


julia> p1 = place("input1", :string)
Place input1 with control token created.


julia> p2 = place("input2",:string)
Place input2 with control token created.


julia> p3 = place("output",:string)
Place output with control token created.


julia> t = transition("trans")
Transition trans created.


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

# If a path is not provided, the generated workflow is stored in the home directory in the folder: tmp
julia> generate_workflow(pn, "/home/pnet/")
An XML workflow called: parallel_reduce.xpnet has been written to the location: /home/pnet/.

```

See also [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref), [`compile_workflow`](@ref).
