```
expansion(model, variable, args...)
```

Defines an expansion variable `variable` within a subproblem `model`. Note that all subproblems must have the same set of expansion variables.

### Required Arguments

`model` is the JuDGE subproblem that we are adding the expansion variable to

`variable` is the name of the variable being created, this will be continuous by default; follows JuMP syntax if defining a set of variables.

### Optional Arguments

This macro has a third, unnamed, argument which can be set to Con, Bin, or Int, similar to the `@variable` macro.

`lag` is the number of nodes in the scenario between an expansion being decided, and it becoming available.

`duration` is the number of consecutive nodes in the scenario over which an expansion is available.

`lb` is the lower bound for this variable in the master problem (typically omitted).

`ub` is the upper bound for this variable in the master problem (typically omitted).

### Examples

```
@expansion(model, expand[1:5], Bin) #defines an array of 5 binary variables with no lag, and unlimited lifespan
@expansion(model, expand[1:5,1:2]>=0, lag=1) #defines a matrix of 10 continuous variables with a lag of 1, and unlimited duration
@expansion(model, 0<=expand<=10, Int, duration=2) #defines a single integer variable with a lag of 0, and a duration of 2
```
