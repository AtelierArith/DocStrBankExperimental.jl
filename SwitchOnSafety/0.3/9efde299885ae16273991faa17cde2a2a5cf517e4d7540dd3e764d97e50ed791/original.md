```
soslyapbs(s::AbstractSwitchedSystem, d::Integer,
          soslb, dual,
          sosub, primal;
          verbose=0, tol=1e-5, step=0.5, scaling=quickub(s),
          ranktols=tol, disttols=tol, kws...)
```

Find the smallest `γ` such that [`soslyap`](@ref) is feasible.
