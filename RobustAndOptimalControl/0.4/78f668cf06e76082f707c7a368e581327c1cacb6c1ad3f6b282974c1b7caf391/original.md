```
named_ss(sys::AbstractStateSpace{T}; x, u, y)
```

Create a `NamedStateSpace` system. This kind of system uses names rather than integer indices to refer to states, inputs and outputs.

  * If a single name is provided but a vector of names is expected, this name will be used as prefix followed by a numerical index.
  * If no name is provided, default names (`x,y,u`) will be used.

# Arguments:

  * `sys`: A system to add names to.
  * `x`: A list of symbols with names of the states.
  * `u`: A list of symbols with names of the inputs.
  * `y`: A list of symbols with names of the outputs.

# Example

```julia
G1 = ss(1,1,1,0)
G2 = ss(1,1,1,0)
s1 = named_ss(G1, x = :x, u = :u1, y=:y1)
s2 = named_ss(G2, x = :z, u = :u2, y=:y2)

s1[:y1, :u1] # Index using symbols. Uses prefix matching if no exact match is found.

fb = feedback(s1, s2, r = :r) # 
```
