```
update_hessian!(d, amp, st, p_old, iter)
```

update the Hessian within the [`QuasiNewtonState`](@ref) `o` given a [`AbstractManoptProblem`](@ref) `amp` as well as the an [`AbstractQuasiNewtonDirectionUpdate`](@ref) `d` and the last iterate `p_old`. Note that the current (`iter`th) iterate is already stored in `o.x`.

See also [`AbstractQuasiNewtonUpdateRule`](@ref) for the different rules that are available within `d`.
