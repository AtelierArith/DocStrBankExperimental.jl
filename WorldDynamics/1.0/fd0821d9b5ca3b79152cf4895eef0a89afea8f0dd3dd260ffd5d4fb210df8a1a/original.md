`plotvariables(solution, xrange, variables::Vector{<:NTuple{4, Any}}; title="", showaxis=true, showlegend=true, linetype="lines", colored=true)`

Plot the values of the variables in the vector `variables` obtained by the ODE system `solution` (normally, obtained by using the `solve` function in `solvesystems.jl`) in the specified `xrange` interval. For each variable, the vector `variables` includes a quadruple, containing the Julia variable, its range, and its symbolic name to be shown in the plot.
