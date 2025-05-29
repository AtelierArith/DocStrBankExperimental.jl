```
solution_size(problem::AbstractProblem, config) -> SolutionSize
```

Size of the `problem` given the configuration `config`. If you have multiple configurations, use `ProblemReductions.solution_size_multiple` instead for better performance.
