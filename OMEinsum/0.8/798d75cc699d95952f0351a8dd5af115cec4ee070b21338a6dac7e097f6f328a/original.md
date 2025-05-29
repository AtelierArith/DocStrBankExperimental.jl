```
getiy(code)
```

Get labels of the output tensor for `EinCode`, `NestedEinsum` and some other einsum like objects. Returns a vector.

```jldoctest; setup = :(using OMEinsum)
julia> getiyv(ein"(ij,jk),k->i")
1-element Vector{Char}:
 'i': ASCII/Unicode U+0069 (category Ll: Letter, lowercase)
```
