```
LinearizingSavingCallback(ils::IndependentlyLinearizedSolution)
LinearizingSavingCallback(ilss::Vector{IndependentlyLinearizedSolution})
```

Provides a saving callback that inserts interpolation points into your signal such that a naive linear interpolation of the resultant saved values will be within `abstol`/`reltol` of the higher-order interpolation of your solution.  This essentially makes a time/space tradeoff, where more points in time are saved, costing more memory, but interpolation is incredibly cheap and downstream algorithm complexity is reduced by not needing to bother with multiple interpolation types.

The algorithm internally checks 3 equidistant points between each time point to determine goodness of fit versus the linearly interpolated function; this should be sufficient for interpolations up to the 4th order, higher orders may need more points to ensure good fit.  This has not been implemented yet.

This callback generator takes in an `IndependentlyLinearizedSolution` object to store output into.  An `IndependentlyLinearizedSolution` object itself controls how many derivatives (if any) to linearize along with the primal states themselves.

Example usage:

```julia
ils = IndependentlyLinearizedSolution(prob)
solve(prob, solver; callback=LinearizingSavingCallback(ils))
```

# Keyword Arguments

  * `interpolate_mask::BitVector`: a set of `u` indices for which the integrator interpolant can be queried. Any false indices will be linearly-interpolated based on the `sol.t` points instead (no subdivision).  This is useful for when a solution needs to ignore certain indices due to badly-behaved interpolation.
