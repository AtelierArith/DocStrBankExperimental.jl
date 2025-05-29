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

This function changes the fields of a problem `::AbstractBifurcationProblem`. For example, you can change the initial condition by doing

```
re_make(prob; u0 = new_u0)
```
