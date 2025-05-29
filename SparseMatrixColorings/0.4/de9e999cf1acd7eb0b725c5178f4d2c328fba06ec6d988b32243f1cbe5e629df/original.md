```
ColoringProblem{structure,partition}
```

Selector type for the coloring problem to solve, enabling multiple dispatch.

It is passed as an argument to the main function [`coloring`](@ref).

# Constructors

```
ColoringProblem{structure,partition}()
ColoringProblem(; structure=:nonsymmetric, partition=:column)
```

  * `structure::Symbol`: either `:nonsymmetric` or `:symmetric`
  * `partition::Symbol`: either `:column`, `:row` or `:bidirectional`

!!! warning
    The second constructor (based on keyword arguments) is type-unstable.


# Link to automatic differentiation

Matrix coloring is often used in automatic differentiation, and here is the translation guide:

|   matrix |    mode |     `structure` |      `partition` | implemented |
| --------:| -------:| ---------------:| ----------------:| -----------:|
| Jacobian | forward | `:nonsymmetric` |        `:column` |         yes |
| Jacobian | reverse | `:nonsymmetric` |           `:row` |         yes |
| Jacobian |   mixed | `:nonsymmetric` | `:bidirectional` |         yes |
|  Hessian |       - |    `:symmetric` |        `:column` |         yes |
|  Hessian |       - |    `:symmetric` |           `:row` |          no |
