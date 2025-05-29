Find the root of the `f` on the bracketing inverval `[x1, x2]` via brent's algo.

##### Arguments

  * `f::Function`: The function you want to bracket
  * `x1::T`: Lower border for search interval
  * `x2::T`: Upper border for search interval
  * `;maxiter::Int(500)`: Maximum number of bisection iterations
  * `;xtol::Float64(1e-12)`: The routine converges when a root is known to lie within `xtol` of the value return. Should be >= 0. The routine modifies this to take into account the relative precision of doubles.
  * `;rtol::Float64(2*eps())`:The routine converges when a root is known to lie within `rtol` times the value returned of the value returned. Should be ≥ 0

##### Returns

  * `x::T`: The found root

##### Exceptions

  * Throws an `ArgumentError` if `[x1, x2]` does not form a bracketing interval
  * Throws a `ConvergenceError` if the maximum number of iterations is exceeded

##### References

Matches `brentq` function from scipy/scipy/optimize/Zeros/bisectq.c
