```
measure(problem::AbstractProblem, measure::AbstractMeasure)::Number
```

Calculate the size of the problem, reducing which serves as the guiding principle for the branching strategy.

### Arguments

  * `problem`: The problem instance.
  * `measure`: The measure of the problem size.

### Returns

A real number representing the problem size.
