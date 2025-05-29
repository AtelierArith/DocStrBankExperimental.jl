```
SemidiscretizationCoupled
```

複数の半離散化を束ねるために使用される構造体です。 [`semidiscretize`](@ref) は、半離散化間で時間ステップを同期させる `ODEProblem` を返します。 `rhs!` の各呼び出しは、各半離散化に対して個別に `rhs!` を呼び出します。半離散化は、[`BoundaryConditionCoupled`](@ref) を使用してメッシュを接合することで結合できます。

!!! warning "実験的なコード"
    これは実験的な機能であり、いつでも変更される可能性があります。

