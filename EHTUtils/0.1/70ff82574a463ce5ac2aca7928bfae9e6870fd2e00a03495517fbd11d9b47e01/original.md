```
unique_ids(itr, sort::Bool=true; keywords...)
```

This is a variant of `unique` function that returns not only a vector of unique elements in the input, but also a vector of the reverse index.

# Arguments

  * `itr`: iterables
  * `sort::Bool`: if the output vector is sorted. Default to `true`.
  * `keywords...`: keywords for `permsort` function considered when `sort == true`.

# Example

```julia
# the original vector
vec = [1,1,3,4,2,3,1,4]

# get unique elements and also the reverse index
uvec, idx = unique_ids(vec) # uvec should be [1,3,4,2]

# this will reconstruct the original vector
rec = uvec[idx]
println(rec == vec)
```
