```
next_k_array!(a)
```

Given an array `a` of k distinct positive integers, sorted in ascending order, return the next k-array in the lexicographic ordering of the descending sequences of the elements, following [Combinatorial number system](https://en.wikipedia.org/wiki/Combinatorial_number_system). `a` is modified in place.

# Arguments

  * `a::Vector{<:Integer}`: Array of length k.

# Returns

  * `a::Vector{<:Integer}`: View of `a`.

# Examples

```julia
julia> n, k = 4, 2;

julia> a = collect(1:2);

julia> while a[end] <= n
           @show a
           next_k_array!(a)
       end
a = [1, 2]
a = [1, 3]
a = [2, 3]
a = [1, 4]
a = [2, 4]
a = [3, 4]
```
