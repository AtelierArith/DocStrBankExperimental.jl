```
 simplify(f::PiecewiseQuadratic)
```

簡略化された区分二次関数 `f` を返します。

区間二次関数 `f_i` と現在の最右の部分は、次の条件を満たす場合に結合され（新しい最右の部分となる）ます。

  * `f_i` または最右の部分のいずれかが点であり、それぞれの下端点と上端点で重なっている場合
  * `f_i` と最右の部分が同じ係数を持ち、それぞれの下端点と上端点で対応している場合（それらは現在、同じ関数の別々の部分です）。

また、無限大またはマイナス無限大で点となる関数は、出現した場合に排除します。

# 例

```jldoctest
julia> f = PiecewiseQuadratic([BoundedQuadratic(-1., 0., 0., -1., 0.),
                                      BoundedQuadratic(0., 0., 0., 0., 0.),
                                      BoundedQuadratic(0., 1., 0., 1., 0.),
                                      BoundedQuadratic(1., 2., 0., 1., 0.),
                                      BoundedQuadratic(3., 5., 1., 1., 1.)])
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = 0, ∀x ∈ [0.00000, 0.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, 1.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [1.00000, 2.00000]
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [3.00000, 5.00000]

julia> simplify(f)
Piecewise quadratic function:
BoundedQuadratic: f(x) = - 1.00000 x , ∀x ∈ [-1.00000, 0.00000]
BoundedQuadratic: f(x) = + 1.00000 x , ∀x ∈ [0.00000, 2.00000]
BoundedQuadratic: f(x) = 1.00000 x² + 1.00000 x + 1.00000, ∀x ∈ [3.00000, 5.00000]

```
