```
theme_joss(; kwargs...)
```

Generate Makie theme for producing figures for JOSS (The Journal of Open Source Software).

The usage is the same as [`theme_acs`](@ref) except figure `width=5.36066`. The value of `width` is obtained from `\uselengthunit{in}\printlength{\linewidth}`.

JOSS is single column, so `theme_joss_1col` and `theme_joss_2col` are not defined.

See also [`theme_acs`](@ref), [`theme_aps`](@ref), [`theme_jcap`](@ref), [`theme_rsc`](@ref), and [`theme_web`](@ref).
