```
Order5()
KumarSinghAkanksha()
```

Implements an order 5 algorithm from *A New Fifth Order Derivative Free Newton-Type Method for Solving Nonlinear Equations* by Manoj Kumar, Akhilesh Kumar Singh, and Akanksha, Appl. Math. Inf. Sci. 9, No. 3, 1507-1513 (2015), DOI: [10.12785/amis/090346](https://doi.org/10.12785/amis/090346). Four function calls per step are needed.  The `Order5` method replaces a Steffensen step with a secant step when `f(x)` is large.

The error, `eᵢ = xᵢ - α`, satisfies `eᵢ₊₁ = K₁ ⋅ K₅ ⋅ M ⋅ eᵢ⁵ + O(eᵢ⁶)`
