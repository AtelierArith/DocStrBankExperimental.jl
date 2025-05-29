````
MBQCInput(indices,values)

- Struct representing an input set into the graph, can be empty

# Parameters
- `indices`: has type Tuple on normally integers (whole numbers 1 to N) and correspond to vertices in a graph.
- `values`: has type Tuple, can be any type

# Example
```
julia> indices = (1,2,3,4)
julia> values = (0,1,1,0) #Computational basis outcomes
julia> mbqc_input = MBQCInput(indices,values)
```
````
