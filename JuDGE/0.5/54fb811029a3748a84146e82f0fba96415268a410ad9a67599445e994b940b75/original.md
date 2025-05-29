```
JuDGEModel(tree::AbstractTree,
           probabilities,
           sub_problem_builder::Function,
           solver;
           discount_factor=1.0,
           risk=RiskNeutral(),
           sideconstraints=nothing,
           check=true,
           perfect_foresight=false)
```

Define a JuDGE model.

### Required arguments

`tree` is a reference to a scenario tree

`probabilities` is either a function, which returns a dictionary of the probabilities of all nodes in a tree, or simply the dictionary itself

`sub_problem_builder` is a function mapping a node to a JuMP model for each subproblems

`solver` is a reference to the optimizer used for the master problem (with appropriate settings);  this can also be a tuple containing two optimizers (one for solving the relaxation, and one for  solving the binary model)

### Optional arguments

`discount_factor` is a number between 0 and 1 defining a constant discount factor along each arc in the scenario tree

`risk` can be either a `Risk` object, or a vector of such objects.

`sideconstraints` is a function which specifies side constraints in the master problem, see [Tutorial 9: Side-constraints](@ref) for further details

`check` is a boolean, which can be set to `false` to disable the validation of the JuDGE model.

`perfect_foresight` is a boolean; this is an experimental feature, which creates an array of JuDGE models, one for each leaf node. This will enable users to easily compute the EVPI for the stochastic program. Also can be used for regret-based risk implementations. See the example EVPI*and*VSS.jl.

### Examples

```
judge = JuDGEModel(tree, ConditionallyUniformProbabilities, sub_problems,
                                Gurobi.Optimizer)
judge = JuDGEModel(tree, probabilities, sub_problems, CPLEX.Optimizer,
                                discount_factor=0.9, risk=Risk(0.5,0.1)))
```
