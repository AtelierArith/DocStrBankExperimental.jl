```
execute_on_input(grammar::AbstractGrammar, program::RuleNode, input::Dict{Symbol, T})::Any where T
```

Converts a `RuleNode` program into an expression using a given `grammar`, then evaluates this expression with a single input dictionary `input` and a symbol table derived from the `grammar` using `execute_on_input(tab::SymbolTable, expr::Any, input::Dict{Symbol, T})`.

# Arguments

  * `grammar::AbstractGrammar`: A grammar object used to convert the `RuleNode` into an executable expression.
  * `program::RuleNode`: The program, represented as a `RuleNode`, to be converted and evaluated.
  * `input::Dict{Symbol, T}`: A dictionary providing input values for symbols used in the generated expression.

# Returns

  * `Any`: The result of evaluating the generated expression with the given input dictionary.
