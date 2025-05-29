bound_remainder(::Type{TaylorModel1}f::Function, polf::Taylor1, polfI::Taylor1, x0::Interval, I::Interval)

Bound the absolute remainder of the polynomial approximation of `f` given by the Taylor polynomial `polf` around `x0` on the interval `I`. It requires the interval extension `polfI` of the polynomial that approximates `f` for the whole interval `I`, in order to compute the Lagrange remainder.

If `polfI[end]` has a definite sign, then it is monotonic in the intervals [I.lo, x0] and [x0.hi, I.hi], which is exploited; otherwise, it is used to compute the Lagrange remainder. This corresponds to Prop 2.2.1 in Mioara Joldes PhD thesis (pp 52).
