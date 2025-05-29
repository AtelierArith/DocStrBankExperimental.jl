```
invert_permutation(p::Vector{<:Integer})
```

Return the inverse of the permutation `p`. 

# Example

```julia-repl
julia> p = [2,1,4,5,3];
julia> p_inv = invert_perm(p); 
julia> show(p_inv)
[4, 2, 5, 1, 6, 3]
julia> show(p_inv[p])
[1, 2, 3, 4, 5, 6]
```
