```
geteqn(i, ssd::SteadyStateData)
```

Return the i-th steady state equation. Index i is interpreted as in the output of [`alleqns(::SteadyStateData)`](@ref). Calling `geteqn(i, sdd)` has the same effect as `alleqn(ssd)[i]`, but it's more efficient.

### Example

```julia
# Iterate all equations like this:
for i = 1:neqns(ssd)
    eqn = geteqn(i, ssd)
    # do something awesome with `eqn` and `i`
end
```
