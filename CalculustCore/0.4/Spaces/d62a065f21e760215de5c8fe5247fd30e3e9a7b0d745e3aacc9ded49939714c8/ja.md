```julia
struct Galerkin <: CalculustCore.Spaces.AbstractDiscretization
```

`Galerkin`離散化は、試行空間がテスト空間と等しい重み付き残差法です。
