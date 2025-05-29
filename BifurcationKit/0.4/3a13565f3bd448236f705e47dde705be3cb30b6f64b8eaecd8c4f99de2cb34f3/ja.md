```julia
re_make(
    prob;
    u0,
    params,
    lens,
    record_from_solution,
    plot_solution,
    J,
    Jᵗ,
    d2F,
    d3F
)

```

この関数は、問題 `::AbstractBifurcationProblem` のフィールドを変更します。たとえば、次のようにして初期条件を変更できます。

```
re_make(prob; u0 = new_u0)
```
