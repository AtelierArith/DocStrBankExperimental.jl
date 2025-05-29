```
FixedDegreePolynomials <: AbstractSymmetricPower
```

固定次数の多項式の空間を表す型。すなわち、変数 $x_1, \dots, x_n$ と次数 $d$ に対して、$\mathbb{F}[x_1, \dots, x_n]_{d}$、次数 $d$ の $n$ 変数の多項式の空間を与えます。

# コンストラクタ

```julia
FixedDegreePolynomials(vars::Vector{<:Variable}, degree::Int)
```

# 例

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
