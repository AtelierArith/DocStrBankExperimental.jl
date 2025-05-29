```
resolve(goals, clauses; <keyword arguments>)
bwd_chain(goals, clauses; <keyword arguments>)
```

SLD-resolution of goals with additional Prolog-like control flow.

# Arguments

  * `goals::Vector{<:Term}`: A list of Julog terms to be prove or query.
  * `clauses::Vector{Clause}`: A list of Julog clauses.
  * `env::Subst=Subst()`: An initial environment mapping variables to terms.
  * `funcs::Dict=Dict()`: Custom functions for evaluating terms. A function `f` should be stored as `funcs[:f] = f`
  * `mode::Symbol=:all`: How results should be returned. `:all` returns all possible substitutions. `:any` returns the first satisfying substitution found. `:interactive` prompts for continuation after each satisfying substitution is found.
  * `search::Symbol=:bfs`: search either breadth (`:bfs`) or depth-first (`:dfs`)
  * `occurs_check::Bool=false`: Flag for occurs check during unification
  * `defer_eval::Bool=false`: Flag to defer evaluation of (custom) operators.
