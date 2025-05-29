```
G = gpath(N, f, name)
```

Generate a GraphSig object for a 1-D path of length `N`

### Input Arguments

  * `N::Int`: the length of the path
  * `f::Matrix{Float64}`: the signal to be used
  * `name::String`: the name for the GraphSig object

### Output Argument

  * `G::GraphSig`: the GraphSig ojbect representing the 1-D path of length `N`
