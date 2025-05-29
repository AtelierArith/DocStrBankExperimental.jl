```
Orthants
```

Iterator to go through all the $2ⁿ$ vectors of length $n$ with elements $±1$. This is equivalento to going through the orthants of an $n$-dimensional euclidean space.

### Fields

n::Int – dimension of the vector space

### Example

```jldoctest
julia> for or in Orthants(2)
       @show or
       end
or = [1, 1]
or = [-1, 1]
or = [1, -1]
or = [-1, -1]
```
