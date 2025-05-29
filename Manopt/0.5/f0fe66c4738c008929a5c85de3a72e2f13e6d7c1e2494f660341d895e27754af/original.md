```
update_hessian!(d::AbstractQuasiNewtonDirectionUpdate, amp, st, p_old, k)
```

update the Hessian within the [`QuasiNewtonState`](@ref) `st` given a [`AbstractManoptProblem`](@ref) `amp` as well as the an [`AbstractQuasiNewtonDirectionUpdate`](@ref) `d` and the last iterate `p_old`. Note that the current (`k`th) iterate is already stored in [`get_iterate`](@ref)`(st)`.

See also [`AbstractQuasiNewtonUpdateRule`](@ref) and its subtypes for the different rules that are available within `d`.
