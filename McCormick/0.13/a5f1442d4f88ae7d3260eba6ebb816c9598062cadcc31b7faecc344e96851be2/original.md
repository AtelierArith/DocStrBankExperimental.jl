```julia
struct MCNoGrad <: Real
```

`MCNoGrad <: Real` is a McCormick structure without RelaxType Tag or subgradients. This structure is used for source-code transformation approaches to constructing McCormick relaxations. Methods definitions and calls should specify the relaxation type used (i.e.) `+(::NS, x::MCNoGrad, y::MCNoGrad)...`. Moreover, the kernel associated with this returns all intermediate calculations necessary to compute subgradient information whereas the overloading calculation simply returns the `MCNoGrad` object. For univariate calculations without tiepoints such as we `log2(::NS, x::MCNoGrad)::MCNoGrad` whereas `log2_kernel(::NS, x::MCNoGrad, ::Bool) = (::MCNoGrad, cv_id::Int, cc_id::Int, dcv, dcc)`. Univariate NS functions follow convention (MCNoGrad, cv*id, cc*id, dcv, dcc, tp1cv, tp1cc, .... tpncv, tpncc) where cv_id is the subgradient selected (1 = cv, 2 = cc, 3 = 0), dcv and dcc are derivatives (or elements of subdifferential) of the outside function evaluated per theorem at the point being evaluated and tpicv, tpicc are the ith tiepoints associated with computing the envelope of the outside function. .

  * `cv::Float64`: Convex relaxation
  * `cc::Float64`: Concave relaxation
  * `Intv::IntervalArithmetic.Interval{Float64}`: Interval bounds
  * `cnst::Bool`: Boolean indicating whether the relaxations are constant over the domain. True if bounding an interval/constant.      False, otherwise. This may change over the course of a calculation `cnst` for `zero(x)` is `true` even if `x.cnst`      is `false`.
