Provides a shorthand for constructing a tight acset transformation by giving its components. Homomorphism search allows partial specification, with the return value being the unique extension if it exists.

Keyword arguments can be passed on to the search function after the body of the transformation.

Example usage for transformation between `WeightedGraph{String}`:

```
@acset_transformation A B begin
  V = [3,5,2] #complete specification can be a vector
  E = Dict(1 => 3, 4 => 3) #otherwise use a dict
end monic=true iso=[:V] or [:V,:E], etc
```
