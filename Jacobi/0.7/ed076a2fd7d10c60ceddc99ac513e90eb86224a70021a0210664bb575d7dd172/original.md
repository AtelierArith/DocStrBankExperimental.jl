```
legendre(x, b)
```

Compute Legendre polynomials.

Legendre polynomials are Jacobi polynomials with parameters a and b equals to zero.

Same interface as `jacobi`. `dlegendre` computes the derivative of the Legendre  polynomial.

# Example

```julia-repl
julia> x = legendre(0.4, 5)
0.27063999999999994

julia> x = legendre(2//5, 5)
3383//12500

julia> x = dlegendre(0.4, 5)
-1.3170000000000002

julia> x = dlegendre(2//5, 5)
-1317//1000
```
