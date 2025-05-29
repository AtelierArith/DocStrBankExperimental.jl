```
FixedMultidegreePolynomials <: AbstractTensorProduct
```

A type representing a space of polynomials of a fixed multidegree in certain groups of variables. For example, for 2 groups of variables $x_1,\dots,x_m$ and $y_1,\dots,y_n$, and degrees $d_1$ and $d_2$, this gives

$$
\mathbb{F}[x_1, \dots, x_m, y_1, \dots, y_n]_{(d_1, d_2)} \cong \mathbb{F}[x_1, \dots, x_m]_{d_1} \otimes \mathbb{F}[y_1, \dots, y_n]_{d_2},
$$

the space of multi-homogeneous polynomials in $m+n$ variables of degree $d_1$ in the first group and  $d_2$ in the second group.

# Constructors

```julia
FixedMultidegreePolynomials(var_groups::Vector{Vector{<:Variable}}, degrees::Vector{Int})
```

# Examples

```jldoctest
julia> @polyvar x[1:3] y[1:2];

julia> V = FixedMultidegreePolynomials([x, y], [1, 1])
FixedMultidegreePolynomials space of dimension 6
 variable groups: [x₁, x₂, x₃], [y₁, y₂]
 multidegree: [1, 1]

julia> fs = factors(V)
2-element Vector{FixedDegreePolynomials{ComplexF64, Commutative{CreationOrder}, Graded{LexOrder}}}:
 FixedDegreePolynomials space of dimension 3
 FixedDegreePolynomials space of dimension 2

julia> fs[2]
FixedDegreePolynomials space of dimension 2
 variables: y₁, y₂
 degree: 1
```
