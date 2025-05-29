```julia
longestcommonsubstring(args; lengthonly)

```

Find the longest common non-empty substring/sub-vector of multiple strings/vectors. 

When there are more than one with the same length, all distinct answers will be returned in a nondeterministic order.

```jldoctest
julia> longestcommonsubstring("ababab", "bababa", "abaabb")
1-element Vector{String}:
 "aba"
```

If keyword argument `lengthonly` is set to `true`, only the length of the longest common substring will be returned.

```jldoctest
julia> longestcommonsubstring("ababab", "bababa", "abaabb"; lengthonly=true)
3
```
