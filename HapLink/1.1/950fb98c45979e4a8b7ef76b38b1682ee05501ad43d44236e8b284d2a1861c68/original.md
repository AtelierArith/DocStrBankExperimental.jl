```
findset(lst::AbstractArray{T}, comparator::Function) where {T}
```

Finds every possible set of items in `lst` where `comparator` returns true for the set.

# Example

```jldoctest
function divisible_by_same_number(x, i)
    for j in 2:i
        if all(y -> y % j == 0, x)
            return true
        end
    end
    return false
end
findset(1:12, x -> divisible_by_same_number(x, 5))

# output
6-element Vector{Vector{Int64}}:
 [2, 4, 6, 8, 10, 12]
 [6, 3, 9, 12]
 [5, 10]
 [1]
 [7]
 [11]
```
