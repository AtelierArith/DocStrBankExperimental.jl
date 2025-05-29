```
pkimport(data, time, obs, sort;
    kelauto = true,
    elimrange = ElimRange(),
    dosetime = DoseTime(),
    limitrule::Union{Nothing, LimitRule} = nothing,
    warn = true,
    kwargs...)
```

Import PK data from table `data`.

  * `time` - time column;
  * `obs` - concentration column;
  * `sort` - subject sorting columns.

keywords:

  * `kelauto` - if `true` auto range settings, if `false` used `kelstart`/`kelend` from `elimrange`;
  * `elimrange` - set elimination range settings;
  * `dosetime` - set dose and dose time, by default dosetime = 0, dose is `NaN`;
  * `limitrule` - apply limitrule to subject;
  * `warn` - false for warnings supress;
  * checktime (true) - check uniqueness of time values;
  * nutcfunk (last) - function used to chose concentration value for identical time (if checktime == `true`).

!!! note
    If time column have non-unique values - last pair time-concentration will be used.


See also: [`ElimRange`](@ref), [`DoseTime`](@ref), [`LimitRule`](@ref).
