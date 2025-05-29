Provides generic asymptotically fast matrix methods:

  * `mul` and `mul!` using the Strassen scheme
  * `_solve_tril!`
  * `lu!`
  * `_solve_triu`

Just prefix the function by "Strassen." all 4 functions support a keyword argument "cutoff" to indicate when the base case should be used.

The speedup depends on the ring and the entry sizes.

# Examples

```jldoctest
julia> m = matrix(ZZ, rand(-10:10, 1000, 1000));

julia> n1 = similar(m); n2 = similar(m); n3 = similar(m);

julia> n1 = mul!(n1, m, m);

julia> n2 = Strassen.mul!(n2, m, m);

julia> n3 = Strassen.mul!(n3, m, m; cutoff = 100);

julia> n1 == n2 == n3
true
```
