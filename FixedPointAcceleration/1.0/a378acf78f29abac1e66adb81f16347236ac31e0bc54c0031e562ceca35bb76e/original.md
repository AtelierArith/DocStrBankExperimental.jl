```
fixed_point(func::Function, previous_FixedPointResults::FixedPointResults;
                Algorithm::Symbol = :Anderson,  ConvergenceMetric::Function  = supnorm(input::Array, output::Array) = maximum(abs.(output .- input)),
                ConvergenceMetricThreshold::R = 1e-10, MaxIter::Integer = Integer(1000), MaxM::Integer = Integer(10), ExtrapolationPeriod::Integer = Integer(7), Dampening::Real = AbstractFloat(1.0),
                PrintReports::Bool = false, ReportingSigFig::Integer = Integer(10), ReplaceInvalids::Symbol = :NoAction, ConditionNumberThreshold::Real = 1e3, quiet_errors::Bool = false) where R<:Real
fixed_point(func::Function, Inputs::Array{T, 1};
                Algorithm::Symbol = :Anderson,  ConvergenceMetric::Function  = supnorm(input::Array, output::Array) = maximum(abs.(output .- input)),
                ConvergenceMetricThreshold::Real = 1e-10, MaxIter::Integer = Integer(1000), MaxM::Integer = Integer(10), ExtrapolationPeriod::Integer = Integer(7), Dampening::Real = AbstractFloat(1.0),
                PrintReports::Bool = false, ReportingSigFig::Integer = Integer(10), ReplaceInvalids::Symbol = :NoAction, ConditionNumberThreshold::Real = 1e3, quiet_errors::Bool = false) where T<:Real
fixed_point(func::Function, Inputs::Real;
                Algorithm::Symbol = :Anderson,  ConvergenceMetric::Function  = supnorm(input::Array, output::Array) = maximum(abs.(output .- input)),
                ConvergenceMetricThreshold::Real = 1e-10, MaxIter::Integer = Integer(1000), MaxM::Integer = Integer(10), ExtrapolationPeriod::Integer = Integer(7), Dampening::Real = AbstractFloat(1.0),
                PrintReports::Bool = false, ReportingSigFig::Integer = Integer(10), ReplaceInvalids::Symbol = :NoAction, ConditionNumberThreshold::Real = 1e3, quiet_errors::Bool = false)
fixed_point(func::Function, Inputs::Array{T, 2}; Outputs::Array{T,2} = Array{T,2}(undef,size(Inputs)[1],0),
                Algorithm::Symbol = :Anderson,  ConvergenceMetric::Function  = supnorm(input::Array, output::Array) = maximum(abs.(output .- input)),
                ConvergenceMetricThreshold::Real = 1e-10, MaxIter::Integer = Integer(1000), MaxM::Integer = Integer(10), ExtrapolationPeriod::Integer = Integer(7), Dampening::Real = AbstractFloat(1.0),
                PrintReports::Bool = false, ReportingSigFig::Integer = Integer(10), ReplaceInvalids::Symbol = :NoAction, ConditionNumberThreshold::Real = 1e3, quiet_errors::Bool = false, other_outputs::Union{Missing,NamedTuple} = missing) where T<:Real where R<:Real
```

A function for finding the fixed point of another function

### Inputs

  * `func` - This is the function for which a fixed point is sought. This function must take and return a vector of the same size dimension.
  * `Inputs` - This can be either a 1D-vector of values that is an initial guess for a fixed point or it can be an N x A matrix of previous inputs for which corresponding outputs are available. In this case N is the dimensionality of the fixed point vector you are seeking (Hence each column is a matrix that is input to f) and A is the number of previous Inputs/Outputs that are being provided to the fixed point. Where a matrix is input, a corresponding outputs must be provided or the last column of the outputs matrix is taken as a startpoint guess and the rest of the inputs and output matrices are discarded.
  * `Outputs` - This is a matrix of the Function values for each column of the input. It must be provided so that column k of the outputs matrix is equal to Function(Column k of inputs matrix).
  * `Algorithm` - This is the fixed point Algorithm to be used. It can be :Anderson, :Simple, :Aitken, :Newton, :MPE, :RRE, :VEA or :SEA. See documentation and references to see explanations of these Algorithms.
  * `ConvergenceMetric` - This is a function that takes in a vector of inputs and a table of outputs and returns a scalar. This scalar should be low when convergence is close to being achieved. By default this is the maximum residual by absolute value (the sup norm in the space of residuals).
  * `ConvergenceMetricThreshold` - This is the threshold for terminating the algorithm. The algorithm will terminate when the scalar that ConvergenceMetric returns is less than ConvergenceMetricThreshold. This can be set to a negative number in which case the algorithm will run until MaxIter is hit or an error occurs (Note that an error is likely in trying to use any Algorithm other than "Simple" when a fixed point is already found).
  * `MaxIter` - This is the maximum number of iterates that will be undertaken.
  * `MaxM` - This is the maximum number of saved iterates that are used in the Anderson algorithm. It has no effect if another Algorithm is chosen. Note that the number of previous iterates that will actually be used is the minimum of MaxIter, the dimensionality of the f's vector and the number of inputs that have been tried to  previously (the width of the Outputs matrix at each given stage of the algorithm). If PrintReports = TRUE, the number of previous iterates actually used is reported as the algorithm is running.
  * `ExtrapolationPeriod` - This is the number of simple iterates to perform before extrapolating. This is used for the MPE, RRE, VEA and SEA Algorithms and has no effect if another Algorithm is chosen Where an epsilon algorithm is used this should be a multiple of 2, ie (4,6,8,etc).
  * `Dampening` - This is the dampening parameter. By default it is 1 which means no dampening takes place. It can also be less than 1 (indicating dampening) or more than 1 (indicating extrapolation).
  * `PrintReports` - This is a boolean describing whether to print ongoing ConvergenceMetric values for each iterate.
  * `ReportingSigFig` - This is the number of significant figures that will be used in printing the convergence values to the console (only if PrintReports is TRUE).
  * `ReplaceInvalids` - Sometimes an acceleration algorithm proposed a vector with an invalid coordinate (NaN, Inf or missing). This parameter can be set to :ReplaceInvalids (to replace invalid coordinates by the simple iterate values), :ReplaceVector (to replace entire vector with a simple iterate) or :NoAction (where an imminent error will occur).
  * `ConditionNumberThreshold` - This is a threshold for what condition number is acceptable for solving the least squares problem for the Anderson Algorithm. If the condition number is larger than this threshold then fewer previous iterates will be used in solving the problem. This has no effect unless the :Anderson Algorithm is used.
  * `quiet_errors` - If true the function will return everything already calculated as soon as an error occurs. The callstack that lead to the error is not returned however. If false an error will be thrown with a callstack.
  * `other_outputs` - This allows you to pass in side products (as in Other*Output* in a FixedPointResults struct). It is only used if the FixedPointResults that is input has already found a fixedpoint.

### Returns

  * A `FixedPointResults` struct containing the fixed_point, the Inputs and corresponding Outputs, and convergence values (which are computed under the "ConvergenceMetric"). The list will also include a "Finish" statement describing why it has finished. This is often going to be due to either MaxIter or ConvergenceMetricThreshold being reached. It may also terminate due to an error in generating a new input guess or using the function with that guess. If this occurs the function will terminate early and the "Finish" statement will describe the issue. In this event there will also be additional objects returned in the list "NewInputVector" and possibly "NewOutputVector" that are useful in debugging the issue.

### Examples

```
# For the simplest possible example we can seek the fixed point of the cos function with a scalar.
Inputs = 0.3
Func(x) = cos(x)
A = fixed_point(Func, Inputs; Algorithm = :Aitken, Dampening = 0.5)
B = fixed_point(Func, Inputs; Algorithm = :Anderson, Dampening = 1.0)

# For this next one the ConvergenceMetricThreshold is negative so the algorithm
# will keep running until MaxIter is met.
C = fixed_point(Func, Inputs; Algorithm = :Simple, MaxIter = 4, ConvergenceMetricThreshold = -1.0)
# But we can continue solving for this fixed point but now switching to the Newton Algorithm.
D = fixed_point(Func, C[:Inputs], C[:Outputs]; Algorithm = :Newton)

# We can also find a 4 dimensional fixed point vector of this function.
Inputs = [0.3, 98, 0, pi]
E = fixed_point(Func, Inputs; Algorithm = :Anderson)
F = fixed_point(Func, Inputs; Algorithm = :Anderson, MaxM = 4, ReportingSigFig = 13)
```
