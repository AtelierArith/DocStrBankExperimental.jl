```
soslyapbs(s::AbstractSwitchedSystem, d::Integer,
          soslb, dual,
          sosub, primal;
          verbose=0, tol=1e-5, step=0.5, scaling=quickub(s),
          ranktols=tol, disttols=tol, kws...)
```

[`soslyap`](@ref) が実行可能であるような最小の `γ` を見つけてください。
