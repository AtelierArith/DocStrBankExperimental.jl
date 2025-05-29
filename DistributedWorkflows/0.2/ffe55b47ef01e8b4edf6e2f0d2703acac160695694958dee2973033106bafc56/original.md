```
savefig(pnet::Workflow_PetriNet)
savefig(pnet::Workflow_PetriNet, format::Symbol)
savefig(pnet::Workflow_PetriNet, path::String)
savefig(pnet::Workflow_PetriNet, format::Symbol, path::String)
```

By default this method generates a PNG file after compiling the Petri net into an XML workflow and compiling the workflow. If path is not given then the workflow image is stored in your home directory in the "tmp/pnet" folder.

Note: Supports all the file formats by GraphViz. For example, :png, :svg, :jpg, :pdf, :webp

For other formats, check GraphViz documentation: https://graphviz.org/docs/outputs/

# Examples

```julia-repl
julia> # first generate a workflow in the form of a Petri net
julia> pn = Workflow_PetriNet("hello_julia")
A Petri net with name "hello_julia", having 0 ports, 0 places, and 0 transitions.


julia> p1 = place("input_file1")
Place "input_file1" created.


julia> p2 = place("input_file2")
Place "input_file2" created.


julia> p3 = place("output_file1")
Place "output_file1" created.


julia> p4 = place("output_file2")
Place "output_file2" created.


julia> t = transition("hello_jl")
Transition "hello_jl" created.


julia> connect(pn,[(p1, :in),(p2, :in),(p3, :out), (p4, :out)], t)
A Petri net with name "hello_julia", having 0 ports, 4 places, and 1 transitions.


julia> connect(pn, p1, :in)
A Petri net with name "hello_julia", having 1 ports, 4 places, and 1 transitions.


julia> connect(pn, p2, :in)
A Petri net with name "hello_julia", having 2 ports, 4 places, and 1 transitions.


julia> connect(pn, p3, :out)
A Petri net with name "hello_julia", having 3 ports, 4 places, and 1 transitions.


julia> connect(pn, p4, :out)
A Petri net with name "hello_julia", having 4 ports, 4 places, and 1 transitions.


julia> pn
A Petri net with name "hello_julia", having 4 ports, 4 places, and 1 transitions.

# now generate the workflow image
julia> savefig(pn, :jpg, "/home/pnet")
"An image of the workflow Petri net could be found in /home/pnet/hello_julia.jpg"

# the following takes the Petri net and the path for storage and generates a PNG file which is stored in the provided path.
julia> savefig(pn, "/home/pnet")
"An image of the workflow Petri net could be found in /home/pnet/hello_julia.png"

```

See also [`Workflow_PetriNet`](@ref), [`place`](@ref), [`transition`](@ref), [`arc`](@ref), [`port`](@ref), [`Workflow_PetriNet`](@ref), [`connect`](@ref), [`remove`](@ref), [`compile_workflow`](@ref), [`generate_workflow`](@ref).
