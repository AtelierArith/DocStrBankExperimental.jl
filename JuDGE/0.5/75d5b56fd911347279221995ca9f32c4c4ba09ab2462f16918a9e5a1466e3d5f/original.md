```
DetEqModel(tree::AbstractTree,
    probabilities,
    sub_problem_builder::Function,
    solver
    discount_factor=1.0,
    risk=RiskNeutral,
    sideconstraints=nothing,
    check=true,
    perfect_foresight = false
)
```

Define a deterministic equivalent model for the stochastic capacity expansion problem.

### Required arguments

`tree` is a reference to a scenario tree

`probabilities` is either a function, which returns a dictionary of the probabilities of all nodes in a tree, or simply the dictionary itself

`sub_problem_builder` is a function mapping a node to a JuMP model for each subproblems

`solver` is a reference to the optimizer used for this problem (with appropriate settings)

### Optional arguments

`discount_factor` is a number between 0 and 1 defining a constant discount factor along each arc in the scenario tree

`risk` is a tuple with the two CVaR parameters: (λ, α)

`sideconstraints` is a function which specifies side constraints in the master problem, see [Tutorial 9: Side-constraints](@ref) for further details.

`check` is a boolean, which can be set to `false` to disable the validation of the JuDGE model.

### Examples

```
deteq = DetEqModel(tree, ConditionallyUniformProbabilities, sub_problems,
                                Gurobi.Optimizer)
judge = DetEqModel(tree, probabilities, sub_problems, CPLEX.Optimizer,
                                discount_factor=0.9, risk=(0.5,0.1)))
```
