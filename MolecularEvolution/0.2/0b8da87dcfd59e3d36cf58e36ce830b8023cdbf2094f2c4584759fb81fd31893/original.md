```
brents_method_minimize(f, a::Real, b::Real, transform, t::Real; ε::Real=sqrt(eps()))
```

Brent's method for minimization.

Given a function f with a single local minimum in the interval (a,b), Brent's method returns an approximation of the x-value that minimizes f to an accuaracy between 2tol and 3tol, where tol is a combination of a relative and an absolute tolerance, tol := ε|x| + t. ε should be no smaller `2*eps`, and preferably not much less than `sqrt(eps)`, which is also the default value. eps is defined here as the machine epsilon in double precision. t should be positive.

The method combines the stability of a Golden Section Search and the superlinear convergence Successive Parabolic Interpolation has under certain conditions. The method never converges much slower than a Fibonacci search and for a sufficiently well-behaved f, convergence can be exptected to be superlinear, with an order that's usually atleast 1.3247...

# Examples

```jldoctest
julia> f(x) = exp(-x) - cos(x)
f (generic function with 1 method)

julia> m = brents_method_minimize(f, -1, 2, identity, 1e-7)
0.5885327257940255
```

From: Richard P. Brent, "Algorithms for Minimization without Derivatives" (1973). Chapter 5.
