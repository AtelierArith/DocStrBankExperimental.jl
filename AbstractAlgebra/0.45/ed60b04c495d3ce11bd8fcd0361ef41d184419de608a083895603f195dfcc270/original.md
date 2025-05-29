```
Perm{T<:Integer}
```

The type of permutations. Fieldnames:

  * `d::Vector{T}` - vector representing the permutation
  * `modified::Bool` - bit to check the validity of cycle decomposition
  * `cycles::CycleDec{T}` - (cached) cycle decomposition

A permutation $p$ consists of a vector (`p.d`) of $n$ integers from $1$ to $n$. If the $i$-th entry of the vector is $j$, this corresponds to $p$ sending $i \to j$. The cycle decomposition (`p.cycles`) is computed on demand and should never be accessed directly. Use [`cycles(p)`](@ref) instead.

There are two inner constructors of `Perm`:

  * `Perm(n::T)` constructs the trivial `Perm{T}`-permutation of length $n$.
  * `Perm(v::AbstractVector{<:Integer} [,check=true])` constructs a permutation represented by `v`. By default `Perm` constructor checks if the vector constitutes a valid permutation. To skip the check call `Perm(v, false)`.

# Examples

```jldoctest
julia> Perm([1,2,3])
()
   
julia> g = Perm(Int32[2,3,1])
(1,2,3)

julia> typeof(g)
Perm{Int32}
```
