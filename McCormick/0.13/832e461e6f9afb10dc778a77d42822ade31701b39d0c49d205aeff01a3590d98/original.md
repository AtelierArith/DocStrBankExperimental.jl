```julia
struct MC{N, T<:McCormick.RelaxTag} <: Real
```

`MC{N, T <: RelaxTag} <: Real` is the McCormick (w/ (sub)gradient) structure which is used to overload standard calculations. The fields are:

  * `cv::Float64`: Convex relaxation
  * `cc::Float64`: Concave relaxation
  * `Intv::IntervalArithmetic.Interval{Float64}`: Interval bounds
  * `cv_grad::StaticArraysCore.SVector{N, Float64} where N`: (Sub)gradient of convex relaxation
  * `cc_grad::StaticArraysCore.SVector{N, Float64} where N`: (Sub)gradient of concave relaxation
  * `cnst::Bool`: Boolean indicating whether the relaxations are constant over the domain. True if bounding an interval/constant.      False, otherwise. This may change over the course of a calculation `cnst` for `zero(x)` is `true` even if `x.cnst`      is `false`.
