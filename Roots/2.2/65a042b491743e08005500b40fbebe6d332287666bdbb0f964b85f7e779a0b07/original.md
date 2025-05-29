```
Secant()
Order1()
Orderφ()
```

The `Order1()` method is an alias for `Secant`. It specifies the [secant method](https://en.wikipedia.org/wiki/Secant_method). This method keeps two values in its state, `xₙ` and `xₙ₋₁`. The updated point is the intersection point of $x$ axis with the secant line formed from the two points. The secant method uses $1$ function evaluation per step and has order `φ≈ (1+sqrt(5))/2`.

The error, `eᵢ = xᵢ - α`, satisfies `eᵢ₊₂ = f[xᵢ₊₁,xᵢ,α] / f[xᵢ₊₁,xᵢ] * (xᵢ₊₁-α) * (xᵢ - α)`.
