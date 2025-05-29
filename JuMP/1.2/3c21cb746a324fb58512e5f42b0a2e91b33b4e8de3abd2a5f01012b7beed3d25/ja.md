```
dual_shape(shape::AbstractShape)::AbstractShape
```

`shape`のオブジェクト空間の双対空間の形状を返します。デフォルトでは、形状の`dual_shape`はそれ自体です。以下の例のセクションでは、これが当てはまらない例を示します。

## 例

双対がモーメント制約であり、モーメント制約の双対が多項式制約である多項式制約を考えます。多項式の形状は次のように定義できます：

```julia
struct Polynomial
    coefficients::Vector{Float64}
    monomials::Vector{Monomial}
end
struct PolynomialShape <: AbstractShape
    monomials::Vector{Monomial}
end
JuMP.reshape_vector(x::Vector, shape::PolynomialShape) = Polynomial(x, shape.monomials)
```

そして、モーメントの形状は次のように定義できます：

```julia
struct Moments
    coefficients::Vector{Float64}
    monomials::Vector{Monomial}
end
struct MomentsShape <: AbstractShape
    monomials::Vector{Monomial}
end
JuMP.reshape_vector(x::Vector, shape::MomentsShape) = Moments(x, shape.monomials)
```

次に、`dual_shape`は多項式およびモーメント制約の双対の形状の定義を可能にします：

```julia
dual_shape(shape::PolynomialShape) = MomentsShape(shape.monomials)
dual_shape(shape::MomentsShape) = PolynomialShape(shape.monomials)
```
