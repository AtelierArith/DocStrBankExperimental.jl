function optimise*linear*sqrtlinear(instance::CombinatorialInstance{T},                                       algo::ESCB2OptimisationAlgorithm,                                       linear::Dict{T, Float64},                                       sqrtlinear::Dict{T, Float64},                                       sqrtlinear*weight::Float64,                                        bandit*round::Int;                                       with_trace::Bool=false) where T

Optimise ESCB2's objective function, with a linear term (with coefficients in `linear`) and a square root (with coefficients in `sqrtlinear`): 

max linear^T x + sqrtlinear_weight * sqrt(sqrtlinear^T x)   s.t. x belongs to the combinatorial set defined by instance

Several implementations are provided, and can be chosen with the appropriate subtype of  `ESCB2OptimisationAlgorithm`.

Returns one (approximately) optimum solution. The exact guarantees depend on the  chosen algorithm. If `with_trace=true`, a second value is returned with comprehensive details of the behaviour of the algorithm.
