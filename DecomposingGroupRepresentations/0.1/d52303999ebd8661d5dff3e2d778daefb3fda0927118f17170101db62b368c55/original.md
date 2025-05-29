```
FixedDegreePolynomials <: AbstractSymmetricPower
```

A type representing a space of polynomials of a fixed degree. I.e., for the variables $x_1, \dots, x_n$ and degree $d$ gives $\mathbb{F}[x_1, \dots, x_n]_{d}$, the space of polynomials in $n$ variables of degree $d$.

# Constructors

```julia
FixedDegreePolynomials(vars::Vector{<:Variable}, degree::Int)
```

# Examples

```jldoctest
julia> @polyvar x[1:3];

julia> V = FixedDegreePolynomials(x, 2)
FixedDegreePolynomials space of dimension 6
 variables: x₁, x₂, x₃
 degree: 2

julia> base_space(V)
VariableSpace with 3 variables
 number type (or field): ComplexF64
 variables: x₁, x₂, x₃

julia> power(V)
2
```
