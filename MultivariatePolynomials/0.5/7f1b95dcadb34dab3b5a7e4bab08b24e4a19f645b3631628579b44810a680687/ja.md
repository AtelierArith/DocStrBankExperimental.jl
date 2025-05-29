```
function filter_terms(f::Function, p::AbstractPolynomialLike)
```

多項式 `p` をフィルタリングし、`f(p)` が `true` となる項 `t` のみを保持します。

関連情報は [`OfDegree`](@ref) を参照してください。

### 例

```julia
julia> p = 1 - 2x + x * y - 3y^2 + x^2 * y
1 - 2x - 3y² + xy + x²y

julia> filter_terms(OfDegree(2), p)
-3y² + xy

julia> filter_terms(!OfDegree(2), p)
1 - 2x + x²y

julia> filter_terms(!OfDegree(0:2), p)
x²y

julia> filter_terms(iseven ∘ coefficient, p)
-2x
```
