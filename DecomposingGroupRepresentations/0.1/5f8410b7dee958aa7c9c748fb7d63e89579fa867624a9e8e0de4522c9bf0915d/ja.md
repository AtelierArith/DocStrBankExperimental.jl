```
FixedMultidegreePolynomials <: AbstractTensorProduct
```

特定の変数群における固定多重次数の多項式の空間を表す型です。例えば、2つの変数群 $x_1,\dots,x_m$ と $y_1,\dots,y_n$、および次数 $d_1$ と $d_2$ に対して、これは次のようになります。

$$
\mathbb{F}[x_1, \dots, x_m, y_1, \dots, y_n]_{(d_1, d_2)} \cong \mathbb{F}[x_1, \dots, x_m]_{d_1} \otimes \mathbb{F}[y_1, \dots, y_n]_{d_2},
$$

最初の群での次数 $d_1$ と2番目の群での次数 $d_2$ の $m+n$ 個の変数の多重同次多項式の空間です。

# コンストラクタ

```julia
FixedMultidegreePolynomials(var_groups::Vector{Vector{<:Variable}}, degrees::Vector{Int})
```

# 例

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
