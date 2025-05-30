```julia
solve(
    ocp::CTModels.Model,
    description::Symbol...;
    kwargs...
)

```

Solve the the optimal control problem `ocp` by the method given by the (optional) description. The available methods are given by `available_methods()`. The higher in the list, the higher is the priority. The keyword arguments are specific to the chosen method and represent the options of the solver.

!!! note
    See the [tutorial on solving optimal control problems](@ref tutorial-solve) for more information.


# Arguments

  * `ocp::OptimalControlModel`: the optimal control problem to solve.
  * `description::Symbol...`: the description of the method to use to solve the problem.
  * `kwargs...`: the options of the solver.

# Examples

The simplest way to solve the optimal control problem is to call the function without any argument.

```julia-rep
julia> sol = solve(ocp)
```

The method can be specified by passing the description as a Symbol. You can provide a partial description, the function will  find the best match.

```julia-rep
julia> sol = solve(ocp, :direct)
```

The method can be specified by passing the full description as a list of Symbols.

```julia-repl
julia> sol = solve(ocp, :direct, :adnlp, :ipopt)
```

The keyword arguments are specific to the chosen method and represent the options of the solver. For example, the keyword `display` is used to display the information of the solver. The default value is `true`.

```julia-rep
julia> sol = solve(ocp, :direct, :ipopt, display=false)
```

The initial guess can be provided by the keyword `init`. You can provide the initial guess for the state, control, and variable.

```julia-rep
julia> sol = solve(ocp, init=(state=[-0.5, 0.2], control=0.5))
```

!!! tip
    For more information on how to provide the initial guess, see the [tutorial on the initial guess](@ref tutorial-initial-guess).

