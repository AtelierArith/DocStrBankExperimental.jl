```
Steffensen()
```

The quadratically converging [Steffensen](https://en.wikipedia.org/wiki/Steffensen's_method#Simple_description) method is used for the derivative-free `Order2()` algorithm. Unlike the quadratically converging Newton's method, no derivative is necessary, though like Newton's method, two function calls per step are. Steffensen's algorithm is more sensitive than Newton's method to poor initial guesses when `f(x)` is large, due to how `f'(x)` is approximated. The `Order2` method replaces a Steffensen step with a secant step when `f(x)` is large.

The error, `eᵢ - α`, satisfies `eᵢ₊₁ = f[xᵢ, xᵢ+fᵢ, α] / f[xᵢ,xᵢ+fᵢ] ⋅ (1 - f[xᵢ,α] ⋅ eᵢ²`
