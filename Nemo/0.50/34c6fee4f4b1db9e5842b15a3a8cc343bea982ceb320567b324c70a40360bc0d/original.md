```
lindep(A::Vector{ArbFieldElem}, bits::Int)
```

Find a small linear combination of the entries of the array $A$ that is small (using LLL). The entries are first scaled by the given number of bits before truncating to integers for use in LLL. This function can be used to find linear dependence between a list of real numbers. The algorithm is heuristic only and returns an array of Nemo integers representing the linear combination.

# Examples

```jldoctest
julia> RR = ArbField(64)
Real Field with 64 bits of precision and error bounds

julia> a = RR(-0.33198902958450931620250069492231652319)
[-0.33198902958450932088 +/- 4.15e-22]

julia> V = [RR(1), a, a^2, a^3, a^4, a^5]
6-element Vector{ArbFieldElem}:
 1.0000000000000000000
 [-0.33198902958450932088 +/- 4.15e-22]
 [0.11021671576446420510 +/- 7.87e-21]
 [-0.03659074051063616184 +/- 4.17e-21]
 [0.012147724433904692427 +/- 4.99e-22]
 [-0.004032911246472051677 +/- 6.25e-22]

julia> W = lindep(V, 20)
6-element Vector{ZZRingElem}:
 1
 3
 0
 0
 0
 1
```
