```
approx(input::FunctionEvaluations{D}, c::Curvature, a::Algorithm)
```

Return PWAFunc{Convex,D} or PWAFunc{Concave,D} depending on `c`, approximating the `input` points in `D` dimensions
