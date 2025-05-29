```
galerkin_matrix!(
    [f::Function], A::AbstractMatrix, B::AbstractBSplineBasis, [deriv = (Derivative(0), Derivative(0))];
    [quadrature],
)
```

事前に割り当てられたガレルキン行列を埋めます。

行列は `Hermitian` ビューである可能性があり、その場合は行列の片側のみが埋められます。行列が対称であるためには、`deriv` の両方の導関数の次数が同じである必要があることに注意してください。

一般的には、`B` として `AbstractBSplineBasis` のタプルを渡すことで、異なる関数基底を組み合わせることが可能です。

引数の詳細については [`galerkin_matrix`](@ref) を参照してください。
