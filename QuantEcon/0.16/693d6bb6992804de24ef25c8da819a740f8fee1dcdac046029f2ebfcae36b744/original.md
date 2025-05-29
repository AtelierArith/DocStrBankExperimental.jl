```
k_array_rank([T=Int], a)
```

Given an array `a` of k distinct positive integers, sorted in ascending order, return its ranking in the lexicographic ordering of the descending sequences of the elements, following [Combinatorial number system](https://en.wikipedia.org/wiki/Combinatorial_number_system).

# Notes

`InexactError` exception will be thrown, or an incorrect value will be returned without warning if overflow occurs during the computation. It is the user's responsibility to ensure that the rank of the input array fits within the range of `T`; a sufficient condition for it is `binomial(BigInt(a[end]), BigInt(length(a))) <= typemax(T)`.

# Arguments

  * `T::Type{<:Integer}`: The numeric type of ranking to be returned.
  * `a::Vector{<:Integer}`: Array of length k.

# Returns

  * `idx::T`: Ranking of `a`.
