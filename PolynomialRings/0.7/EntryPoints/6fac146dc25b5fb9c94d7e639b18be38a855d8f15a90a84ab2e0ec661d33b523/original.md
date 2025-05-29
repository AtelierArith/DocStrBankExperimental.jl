```
polynomial_ring(symbols::Symbol...; basering=Rational{BigInt}, exptype=Int16, monomialorder=:degrevlex)
```

Create a type for the polynomial ring over `basering` in variables with names specified by `symbols`, and return the type and a tuple of these variables.

The `exptype` parameter defines the integer type for the exponents.

The `monomialorder` defines an order for the monomials for e.g. Gröbner basis computations; it also defines the internal sort order. Built-in values are `:degrevlex`, `:deglex` and `:lex`. This function will accept any symbol, though, and you can define your own monomial order by implementing

```
Base.Order.lt(::MonomialOrder{:myorder}, a::M, b::M) where M <: AbstractMonomial
```

See `PolynomialRings.MonomialOrderings` for examples.

# Examples

```jldoctest
julia> using PolynomialRings

julia> R,(x,y,z) = polynomial_ring(:x, :y, :z);

julia> x*y + z
x*y + z
```
