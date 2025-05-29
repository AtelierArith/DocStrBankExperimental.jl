```
execute_on_input(tab::SymbolTable, expr::Any, input::Vector{T})::Vector{<:Any} where T <: Dict{Symbol, <:Any}
```

Wrapper around [`execute_on_input`](@ref) to execute all inputs given as an array.

# Arguments

  * `tab::SymbolTable`: A symbol table containing predefined symbols and their associated values or functions.
  * `expr::Any`: The expression to be evaluated for each input dictionary.
  * `inputs::Vector{T}`: A vector of dictionaries, each serving as an individual set of inputs for the expression's evaluation.

# Returns

  * `Vector{<:Any}`: A vector containing the results of evaluating the expression for each input dictionary.
