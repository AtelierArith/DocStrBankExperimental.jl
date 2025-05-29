````
MBQCAngles(angles) 

- Struct representing the angles associated to the graph. The number of angles will be the same as the vertices in the graph.

# Parameters
- `angles`: A listed set of values, as long as the angles are indexable in the same ways that the vertices are.

# Example
```
julia> angles = [π,π/4,5π/4,7π/4]
julia> mbqc_angles = MBQCAngles(angles) 
```
````
