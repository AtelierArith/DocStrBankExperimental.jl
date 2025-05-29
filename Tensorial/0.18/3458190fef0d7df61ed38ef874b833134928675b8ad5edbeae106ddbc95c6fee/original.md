```
hessian(f, x)
hessian(f, x, :all)
```

Compute the hessian of `f` with respect to `x` by the automatic differentiation. If pseudo keyword `:all` is given, the value of `f(x)` is also returned.

# Examples

```jldoctest
julia> x = rand(Vec{3})
3-element Vec{3, Float64}:
 0.32597672886359486
 0.5490511363155669
 0.21858665481883066

julia> hessian(norm, x)
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
  1.13603   -0.582196  -0.231782
 -0.582196   0.501079  -0.390397
 -0.231782  -0.390397   1.32626

julia> ∇∇f, ∇f, f = hessian(norm, x, :all)
([1.1360324375454411 -0.5821964220304534 -0.23178236037013888; -0.5821964220304533 0.5010791569244991 -0.39039709608344814; -0.23178236037013886 -0.39039709608344814 1.3262640626479867], [0.4829957515506539, 0.8135223859352438, 0.3238771859304809], 0.6749059962060727)
```
