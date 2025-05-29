`coxeter_group(C)` or `coxgroup(C)`

`C`  should be  a square  matrix of  integers, rationals or real cyclotomic numbers.  The function returns the Coxeter group whose Cartan matrix is `C` as  a matrix group with the following  generators. Let `V` be a real vector space  of dimension `size(C,1)` and let `eᵢ` be the canonical basis of `V`. Then the generators are the reflections `sᵢ(eⱼ)=eⱼ-Cᵢⱼ eᵢ`.

```julia-repl
julia> W=coxgroup([2 -2;-2 2])
coxeter_group([2 -2; -2 2])

julia> gens(W) # the matrix generators
2-element Vector{Matrix{Int64}}:
 [-1 0; 2 1]
 [1 2; 0 -1]
```

Above is a way to construct the affine Weyl group  `Ã₁`.
