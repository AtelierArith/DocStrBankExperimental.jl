```
struct AdaptiveReduction{A,B,R<:DirectReduction{A,B}} <: GreedyReduction{A,B}
  reduction::R
  adaptive_nparams::Int
  adaptive_tol::Float64
  adaptive_maxiter::Int
end
```

Not implemented yet. Will serve as a parameter-adaptivity greedy reduction algorithm
