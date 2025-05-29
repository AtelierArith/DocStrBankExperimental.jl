```
nthperm(p)
```

Return the integer `k` that generated permutation `p`. Note that `nthperm(nthperm([1:n], k)) == k` for `1 <= k <= factorial(n)`.

# Examples

```jldoctest
julia> nthperm(nthperm([1:3...], 4))
4

julia> collect(permutations([1, 2, 3]))
6-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [1, 3, 2]
 [2, 1, 3]
 [2, 3, 1]
 [3, 1, 2]
 [3, 2, 1]

julia> nthperm([1, 2, 3])
1

julia> nthperm([3, 2, 1])
6

julia> nthperm([1, 1, 1])
ERROR: ArgumentError: argument is not a permutation
[...]

julia> nthperm(collect(1:10))
1

julia> nthperm(collect(10:-1:1))
3628800
```
