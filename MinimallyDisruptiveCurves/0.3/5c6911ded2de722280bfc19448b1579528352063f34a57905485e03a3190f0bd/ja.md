`v = Verbose(a::Vector{T}) where T <: CallbackCallable`

例: `v = Verbose([HamiltonianResidual(0.1:2.:10), CurveDistance(0.1:0.1:5)]) evolve(c::MDCProblem, ...; mdc_callback=[v, other_mdc_callbacks])``この場合、曲線が進化する際にREPL出力が得られ、曲線が`0.1:0.1:5`の各距離に達したときに示され、理想的にはゼロであるべきdHduの残差が示されます。`0.1:0.1:5`で。
