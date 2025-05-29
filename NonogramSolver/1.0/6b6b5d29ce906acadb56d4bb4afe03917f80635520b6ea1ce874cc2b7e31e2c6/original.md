```
solve_puzzle(p::Puzzle) -> PuzzleSolution

solve_puzzle(
    p::Puzzle,
    auxQs::AuxPuzzleQuantities = eval_aux_quantities(p);
    optimizer = GLPK.Optimizer,
    solverAttributes = ("msg_lev" => GLPK.GLP_MSG_OFF,),
    verbosity::Int = 1
) -> PuzzleSolution
```

Solve the [`Puzzle`](@ref) `p`, and construct a corresponding [`PuzzleSolution`](@ref).

This puzzle is solved according to a [method by Khan](https://doi.org/10.1109/TG.2020.3036687), using an integer linear programming (ILP) solver in the optimization framework JuMP. If successful, returns one solution. Uses the freely available solver GLPK by default. All arguments other than `p` are optional.

The puzzle instance `p` may be constructed using either a [`Puzzle`](@ref) constructor or [`read_puzzle_from_cwc`](@ref). The arguments `optimizer` and `solverAttributes` specify your choice of ILP solver and settings to JuMP, for use in JuMP's command:

```
JuMP.optimizer_with_attributes(optimizer, solverAttributes...)
```

See JuMP's documentation for more details about setting up these inputs. 

Reports JuMP's solution summary by default; set `verbosity=0` to suppress this.
