`objgrad!(f, t, g)` evaluates the objective and first derivative of the `LineModel`

```
ϕ(t) := f(x + td),
```

and

```
ϕ'(t) = ∇f(x + td)ᵀd.
```

The gradient ∇f(x + td) is stored in `g`.
