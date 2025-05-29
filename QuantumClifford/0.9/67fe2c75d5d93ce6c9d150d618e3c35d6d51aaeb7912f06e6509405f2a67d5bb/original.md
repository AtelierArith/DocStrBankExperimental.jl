Embed a Pauli operator in a larger Pauli operator.

```jldoctest
julia> embed(5, 3, P"-Y")
- __Y__

julia> embed(5, (3,5), P"-YX")
- __Y_X
```
