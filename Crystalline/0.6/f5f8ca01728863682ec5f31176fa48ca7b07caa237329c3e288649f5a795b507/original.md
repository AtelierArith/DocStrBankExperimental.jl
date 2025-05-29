```
israyrep(lgir::LGIrrep, αβγ=nothing) -> (::Bool, ::Matrix)
```

Computes whether a given little group irrep `ir` is a ray representation  by computing the coefficients αᵢⱼ in DᵢDⱼ=αᵢⱼDₖ; if any αᵢⱼ differ  from unity, we consider the little group irrep a ray representation (as opposed to the simpler "vector" representations where DᵢDⱼ=Dₖ). The function returns a boolean (true => ray representation) and the coefficient matrix αᵢⱼ.
