`approx_in(x, domain::Domain [, tolerance])`

Verify whether a point lies in the given domain with a certain tolerance.

The tolerance has to be positive. The meaning of the tolerance, in relation to the possible distance of the point to the domain, is domain-dependent. Usually, if the outcome is true, it means that the distance of the point to the domain is smaller than a constant times the tolerance. That constant may depend on the domain.

Up to inexact computations due to floating point numbers, it should also be the case that `approx_in(x, d, 0) == in(x,d)`. This implies that `approx_in` reflects whether a domain is open or closed.
