```
gauss(J::AbstractMatrix, unitintegral::Real=1, [ (a₀,b₀) => (a,b) ])
```

Construct the $n$-point Gaussian quadrature rule for $I[f] = \int_a^b w(x) f(x) dx$ from the $n \times n$ symmetric tridiagonal Jacobi matrix `J` corresponding to the orthogonal polynomials for that weighted integral.  The value of `unitintegral` should be $I[1]$, the integral of the weight function.

An optional argument `(a₀,b₀) => (a,b)` allows you to specify that `J` was originally defined for a different interval $(a_0, b_0)$, which you want to rescale to a given $(a, b)$.  (`gauss` will rescale the points and weights for you.)

Returns a pair `(x, w)` of $n$ quadrature points `x[i]` and weights `w[i]` to integrate functions, i.e. `sum(w .* f.(x))` approximates the integral $I[f]$.
