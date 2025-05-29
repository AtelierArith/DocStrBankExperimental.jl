```
getixsv(code)
```

Get labels of input tensors for `EinCode`, `NestedEinsum` and some other einsum like objects. Returns a vector of vectors.

```jldoctest; setup = :(using OMEinsum)
julia> getixsv(ein"(ij,jk),k->i")
3-element Vector{Vector{Char}}:
 ['i', 'j']
 ['j', 'k']
 ['k']
```
