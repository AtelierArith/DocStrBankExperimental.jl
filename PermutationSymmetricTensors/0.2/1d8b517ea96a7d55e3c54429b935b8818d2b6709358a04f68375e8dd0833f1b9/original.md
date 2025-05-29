function find*full*indices(N, dim)

```
Returns an ordered array of tuples of indices (i1, i2, i3, ..., i{dim}) such that 
i1 >= i2 >= i3 ... >= i{dim}. This can be used to find the cartesian index that 
corresponds to a linear index of a SymmetricTensor{T, N, dim}. 
Example:
julia> find_full_indices(3, 3)
10-element Vector{Tuple{Int8, Int8, Int8}}:
(1, 1, 1)
(2, 1, 1)
(3, 1, 1)
(2, 2, 1)
(3, 2, 1)
(3, 3, 1)
(2, 2, 2)
(3, 2, 2)
(3, 3, 2)
(3, 3, 3)

It is implemented with a generated function, for dim = 3, the following code will be executed:
function _find_full_indices(N, Val(3))
    full_indices = NTuple{3, Int16}[]
    for i3 = 1:N
        for i2 = i3:N
            for i1 = i2:N
                push!(full_indices, ((i1..., i2)..., i3))
            end
        end
    end
    full_indices
end
```
