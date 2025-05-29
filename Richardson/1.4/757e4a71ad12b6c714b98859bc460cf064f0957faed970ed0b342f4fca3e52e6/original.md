The `Richardson` module provides a function `extrapolate` that extrapolates a given function `f(x)` to `f(x0)`, evaluating `f` only  at a geometric sequence of points `> x0` (or optionally `< x0`).

The key algorithm is Richardson extrapolation using a Neville—Aitken tableau, which adaptively increases the degree of an extrapolation polynomial until convergence is achieved to a desired tolerance (or convergence stalls due to e.g. floating-point errors).  This allows one to obtain `f(x0)` to high-order accuracy, assuming that `f(x0+h)` has a Taylor series or some other power series in `h`.
