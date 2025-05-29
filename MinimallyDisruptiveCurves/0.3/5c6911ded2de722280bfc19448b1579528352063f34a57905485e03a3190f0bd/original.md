Construct as `v = Verbose(a::Vector{T}) where T <: CallbackCallable`

Example: `v = Verbose([HamiltonianResidual(0.1:2.:10), CurveDistance(0.1:0.1:5)]) evolve(c::MDCProblem, ...; mdc_callback=[v, other_mdc_callbacks])``In this case, you would get REPL output as the curve evolved, indicating when the curve reached each distance in`0.1:0.1:5`, and indicating the residual on dHdu, which is ideally zero, at`0.1:0.1:5`.
