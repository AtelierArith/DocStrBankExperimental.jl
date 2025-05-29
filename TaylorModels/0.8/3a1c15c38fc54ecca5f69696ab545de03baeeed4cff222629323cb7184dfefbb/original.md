bound_remainder(::Type{RTaylorModel1}, f::Function, polf::Taylor1, polfI::Taylor1, x0::Interval, I::Interval)

Bound the relative remainder of the polynomial approximation of `f` given by the Taylor polynomial `polf` around `x0` on the interval `I`. It requires an the interval extension `polfI` of a polynomial that approximates `f` for the whole interval `I`, in order to compute the Lagrange remainder.

If `polfI[end]` has a definite sign, then it is monotonic in the interval `I`, which is exploited; otherwise, the last coefficients bounds the relative remainder. This corresponds to Prop 2.3.7 in Mioara Joldes' PhD thesis (pp 67).
