```
@NLobjective(model, sense, expression)
```

Add a nonlinear objective to `model` with optimization sense `sense`. `sense` must be `Max` or `Min`.

# Example

```
@NLobjective(model, Max, 2x + 1 + sin(x))
```
