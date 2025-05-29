ARTrustRegion(α₀::T;kwargs...)

Select the main parameters used in the `TRARC` algorithm with `α₀` as initial TR/ARC parameter. The keyword arguments are:

  * `max_α::T`: Maximum value for `α`. Default `T(1) / sqrt(eps(T))`.
  * `acceptance_threshold::T`: Ratio over which the step is successful. Default `T(0.1)`.
  * `increase_threshold::T`: Ratio over which we increase `α`. Default `T(0.75)`.
  * `reduce_threshold::T`: Ratio under which we decrease `α`. Default `T(0.1)`.
  * `increase_factor::T`: Factor of increase of `α`. Default `T(5.0)`.
  * `decrease_factor::T`: Factor of decrease of `α`. Default `T(0.1)`.
  * `max_unsuccinarow::Int`: Limit on the number of successive unsucessful iterations. Default `30`.

Returns a `ARTrustRegion` structure.

This can be compared to `TrustRegion` or `TRONTrustRegion`.
