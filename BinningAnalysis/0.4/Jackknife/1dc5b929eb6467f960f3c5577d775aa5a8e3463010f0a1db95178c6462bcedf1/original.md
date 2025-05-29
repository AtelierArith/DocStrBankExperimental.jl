**Jackknife** errors for (non-linear) functions of uncertain data, i.e. `g(<a>, <b>, ...)` where `<a>`, `<b>` are the means of data sets `a` and `b`. Use `jackknife_full(g, a, b, ...)` to get the jackknife estimate, bias and error or `jackknife(g, a, b, ...)` to get just the estimate and error.

See: [`jackknife_full`](@ref), [`jackknife`](@ref)
