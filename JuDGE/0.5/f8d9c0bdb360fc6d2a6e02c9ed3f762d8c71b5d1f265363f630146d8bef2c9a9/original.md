```
state(model, variable, args...)
```

Defines a state variable `variable` within a subproblem `model`. Note that all subproblems must have the same set of state variables. These variables can be used to model inventory that is carried forward between the subproblems.

### Required Arguments

`model` is the JuDGE subproblem that we are adding the expansion variable to

`variable` is the name of the variable being created in the subproblem, this will be continuous by default; follows JuMP syntax if defining a set of variables. The subproblem variable corresponds to the change in the state.

### Optional Arguments

This macro has a third, unnamed, argument which can be set to Con, Bin, or Int, similar to the `@variable` macro.

`state_name` is the name for the state variable in the master problem. If omitted, the name of the master problem variable will match the subproblem variable (but this may cause confusion, since only the master problem variable is the state). See the `inventory.jl` example to see how this should be implemented.

`initial` is the initial value for the master problem's state variable at the root node.

`lb` is the lower bound for the variable in the master problem (typically omitted).

`ub` is the upper bound for the variable in the master problem (typically omitted).

### Examples

```
@state(sp, -50<=Δstock<=50, state_name=stock, lb=0, ub=200, initial=0) #defines a state variable called stock in the master
                                                                       #(starting at 0, and able to take values 0 to 200),
                                                                       #and Δstock in the subproblem (able to change the stock level by ±50).
```
