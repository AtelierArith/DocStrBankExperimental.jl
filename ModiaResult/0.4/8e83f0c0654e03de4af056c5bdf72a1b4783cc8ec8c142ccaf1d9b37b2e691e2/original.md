```
(xsig, xsigLegend, ysig, ysigLegend, ysigType) = getPlotSignal(result, ysigName; xsigName=nothing)
```

Given the result data structure `result` and a variable `ysigName::AbstractString` with or without array range indices (for example `ysigName = "a.b.c[2,3:5]"`) and an optional variable name `xsigName::AbstractString` for the x-axis, return

  * `xsig::Vector{T1<:Real}`: The vector of the x-axis signal without a unit. Segments are concatenated and separated by NaN.
  * `xsigLegend::AbstractString`: The legend of the x-axis consisting of the x-axis name and its unit (if available).
  * `ysig::Vector{T2}` or `::Matrix{T2}`: the y-axis signal, either as a vector or as a matrix of values without units depending on the given name. For example, if `ysigName = "a.b.c[2,3:5]"`, then `ysig` consists of a matrix with three columns corresponding to the variable values of `"a.b.c[2,3]", "a.b.c[2,4]", "a.b.c[2,5]"` with the (potential) units are stripped off. Segments are concatenated and separated by NaN.
  * `ysigLegend::Vector{AbstractString}`: The legend of the y-axis as a vector of strings, where `ysigLegend[1]` is the legend for `ysig`, if `ysig` is a vector, and `ysigLegend[i]` is the legend for the i-th column of `ysig`, if `ysig` is a matrix. For example, if variable `"a.b.c"` has unit `m/s`, then `ysigName = "a.b.c[2,3:5]"` results in `ysigLegend = ["a.b.c[2,3] [m/s]", "a.b.c[2,3] [m/s]", "a.b.c[2,5] [m/s]"]`.
  * `ysigType::`[`SignalType`](@ref): The signal type of `ysig` (either `ModiaResult.Continuous` or `ModiaResult.Clocked`).

If `ysigName` is not valid, or no signal values are available, the function returns `(nothing, nothing, nothing, nothing, nothing)`, and prints a warning message.
