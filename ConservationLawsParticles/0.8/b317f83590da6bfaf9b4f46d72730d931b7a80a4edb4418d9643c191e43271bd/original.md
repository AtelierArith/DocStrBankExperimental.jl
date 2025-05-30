Automatically define a method which takes time as first argument and discards it.

# Examples

The definition

```julia
@time_independent V(x) = -x^3
```

is equivalent to

```julia
V(x) = -x^3
V(t, x) = V(x)
```

This also works with more than one argument, for instance

```julia
@time_independent V(x₁, x₂) = x₁ * x₂
```

is equivalent to

```julia
V(x₁, x₂) = x₁ * x₂
V(t, x₁, x₂) = V(x₁, x₂)
```
