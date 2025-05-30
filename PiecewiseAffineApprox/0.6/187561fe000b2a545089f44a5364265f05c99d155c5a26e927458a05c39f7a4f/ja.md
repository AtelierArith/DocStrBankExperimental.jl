```
approx(input::FunctionEvaluations{D}, c::Curvature, a::Algorithm)
```

`input`の点をD次元で近似し、`c`に応じてPWAFunc{Convex,D}またはPWAFunc{Concave,D}を返します。
