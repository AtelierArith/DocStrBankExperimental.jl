```
enforced(model, variable, args...)
```

Defines an enforced variable `variable` within a subproblem `model`. Note that all subproblems must have the same set of enforced variables. These variables can be used as either expansion or shutdown variables, but since the constraint in the master problem is an equality, convergence is more difficult since there is less flexibility when solving the master problem.

### Required Arguments

`model` is the JuDGE subproblem that we are adding the expansion variable to

`variable` is the name of the variable being created, this will be continuous by default; follows JuMP syntax if defining a set of variables.

### Optional Arguments

This macro has a third, unnamed, argument which can be set to Con, Bin, or Int, similar to the `@variable` macro.

`lag` is the number of nodes in the scenario between an expansion being decided, and it becoming available.

`duration` is the number of consecutive nodes in the scenario over which an expansion is available.

`lb` is the lower bound for this variable in the master problem (typically omitted).

`ub` is the upper bound for this variable in the master problem (typically omitted).

`penalty` is a placeholder for a future feature, which may allow the violation of master/subproblem equality constraint, at a cost.

### Examples

```
@expansion(model, forced[1:5], Bin) #defines an array of 5 binary variables with no lag, and unlimited lifespan
@expansion(model, forced[1:5,1:2]>=0, lag=1) #defines a matrix of 10 continuous variables with a lag of 1, and unlimited duration
@expansion(model, 0<=forced<=10, Int, duration=2) #defines a single integer variable with a lag of 0, and a duration of 2
```
