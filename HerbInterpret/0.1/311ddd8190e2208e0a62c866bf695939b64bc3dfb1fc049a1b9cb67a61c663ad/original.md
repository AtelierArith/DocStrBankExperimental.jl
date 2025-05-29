```
execute_on_input(grammar::AbstractGrammar, program::RuleNode, input::Vector{T})::Vector{Any} where T <: Dict{Symbol, <:Any}
```

Converts a `RuleNode` program into an expression using a given `grammar`, then evaluates this expression for each input dictionary in a vector `input` and a symbol table derived from the `grammar` using `execute_on_input(tab::SymbolTable, expr::Any, input::Dict{Symbol, T})`.

# Arguments

  * `grammar::AbstractGrammar`: A grammar object used to convert the `RuleNode` into an executable expression.
  * `program::RuleNode`: The program, represented as a `RuleNode`, to be converted and evaluated.
  * `input::Vector{T}`: A vector of dictionaries, each providing input values for symbols used in the generated expression.

# Returns

  * `Vector{Any}`: A vector containing the results of evaluating the generated expression for each input dictionary.
