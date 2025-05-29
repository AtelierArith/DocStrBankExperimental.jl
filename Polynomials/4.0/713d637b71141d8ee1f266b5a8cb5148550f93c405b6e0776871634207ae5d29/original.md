```
printpoly(io::IO, p::AbstractPolynomial, mimetype = MIME"text/plain"(); descending_powers=false, offset::Int=0, var=indeterminate(p), compact=false, mulsymbol="*")
```

Print a human-readable representation of the polynomial `p` to `io`. The MIME types "text/plain" (default), "text/latex", and "text/html" are supported. By default, the terms are in order of ascending powers, matching the order in `coeffs(p)`; specifying `descending_powers=true` reverses the order. `offset` allows for an integer number to be added to the exponent, just for printing. `var` allows for overriding the variable used for printing. Setting `mulsymbol=""` will avoid an operator being printed. Setting `compact=true` will use a compact style for floating point numbers.

# Examples

```jldoctest show
julia> using Polynomials

julia> printpoly(stdout, Polynomial([1,2,3], :y))
1 + 2*y + 3*y^2

julia> printpoly(stdout, Polynomial([1,2,3], :y), descending_powers=true)
3*y^2 + 2*y + 1

julia> printpoly(stdout, Polynomial([2, 3, 1], :z), descending_powers=true, offset=-2)
1 + 3*z^-1 + 2*z^-2

julia> printpoly(stdout, Polynomial([-1, 0, 1], :z), offset=-1, descending_powers=true)
z - z^-1

julia> printpoly(stdout, Polynomial([-1, 0, 1], :z), offset=-1, descending_powers=true, var=:x)
x - x^-1

julia> p = Polynomial([sqrt(i) for i in 1:4])
Polynomial(1.0 + 1.4142135623730951*x + 1.7320508075688772*x^2 + 2.0*x^3)

julia> printpoly(stdout, p, compact=true)
1.0 + 1.41421*x + 1.73205*x^2 + 2.0*x^3

julia> printpoly(stdout, map(x -> round(x, digits=12), p))  # more control on rounding
1.0 + 1.414213562373*x + 1.732050807569*x^2 + 2.0*x^3
```
