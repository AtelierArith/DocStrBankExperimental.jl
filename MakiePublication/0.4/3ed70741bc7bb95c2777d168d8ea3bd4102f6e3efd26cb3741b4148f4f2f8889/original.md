```
theme_jhep(; kwargs...)
```

Generate Makie theme for producing figures for JHEP (Journal of High Energy Physics).

The usage is the same as [`theme_acs`](@ref) except figure `width=5.95393`. The value of `width` is obtained from `\uselengthunit{in}\printlength{\linewidth}`.

JHEP is single column, so `theme_jhep_1col` and `theme_jhep_2col` are not defined.

See also [`theme_acs`](@ref), [`theme_aps`](@ref), [`theme_jcap`](@ref), [`theme_rsc`](@ref), and [`theme_web`](@ref).
