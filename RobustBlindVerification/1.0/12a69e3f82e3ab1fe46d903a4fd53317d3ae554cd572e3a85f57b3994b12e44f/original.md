````
MBQCGraph(graph,input,output)

- Struct representing the graph used in the MBQC. Container holds the graph as well as the input and output sets.

# Parameters
- `graph`: Any graph suitable for MBQC
- `input`: has type MBQCInput
- `output`: had type MBQCOutput

# Example
```
julia> using Graphs # use using Pkg; Pkg.add("Graphs") is not installede
julia> graph = Graphs.grid([1,4]) # 1D cluster graph (path graph) on 4 vertices
julia> indices,values = (1),(0)
julia> input  = MBQCInput(indices,values)
julia> indices = (4)
julia> output  = MBQCOutput(indices)
julia> mbqc_graph = MBQCGraph(graph,input,output)
```
````
