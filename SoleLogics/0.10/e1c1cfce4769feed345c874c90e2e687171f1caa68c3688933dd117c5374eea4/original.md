```
parseformula(
    [F::Type{<:Formula}=SyntaxTree],
    expr::String,
    additional_operators::Union{Nothing,AbstractVector} = nothing;
    kwargs...
)::F

parseformula(
    F::Type{<:SyntaxTree},
    expr::String,
    logic::AbstractLogic;
    kwargs...
)::F
```

Parse a formula of type `F` from a string expression (its [`syntaxstring`](@ref)).

By default, this function is only able to parse operators in [`SoleLogics.BASE_PARSABLE_CONNECTIVES`](@ref) (e.g., ¬, ∧, ∨ and →); additional, non-standard operators may be provided as a vector `additional_operators`, and their `syntaxstring`s will be used for parsing them. Note that, in case of clashing `syntaxstring`s, the provided additional operators will override the standard ones.

When parsing `SyntaxTree`s, the [Shunting yard](https://en.wikipedia.org/wiki/Shunting_yard_algorithm) algorithm is used, and the method allows the following keywords arguments.

# Keyword Arguments

  * `function_notation::Bool = false`: if set to `true`, the expression is considered   in function notation (e.g., `"⨁(arg1, arg2)"`);   otherwise, it is considered in   [infix notation](https://en.wikipedia.org/wiki/Infix_notation) (e.g., `"arg1 ⨁ arg2"`);
  * `atom_parser::Base.Callable = Atom{String}`: a callable to be used for   parsing atoms, once they are recognized in the expression. It must return   the atom, or the `Atom` itself;
  * `additional_whitespaces::Vector{Char} = Char[]`: characters to be stripped out from each   syntax token.   For example, if `'@' in additional_whitespaces`, "¬@p@" is parsed just as "¬p".
  * `opening_parenthesis::String = "("`:   the string signaling the opening of an expression block;
  * `closing_parenthesis::String = ")"`:   the string signaling the closing of an expression block;
  * `arg_delim::String = ","`:   when `function_notation = true`,   the string that delimits the different arguments of a function call.

!!! warning
    For a proper functioning, the `syntaxstring` of any syntax token cannot be prefixed/suffixed by whitespaces. For example, for any operator `⨁`, it should hold that `syntaxstring(⨁) == strip(syntaxstring(⨁))`. Also, `syntaxstring`s cannot contain special symbols (`opening_parenthesis`, `closing_parenthesis`, and `arg_delim`) as substrings.


# Examples

```julia-repl
julia> syntaxstring(parseformula("¬p∧q∧(¬s∧¬z)"))
"¬p ∧ q ∧ ¬s ∧ ¬z"

julia> syntaxstring(parseformula("∧(¬p,∧(q,∧(¬s,¬z)))", function_notation=true))
"¬p ∧ q ∧ ¬s ∧ ¬z"

julia> syntaxstring(parseformula("¬1→0"; atom_parser = (x -> Atom{Float64}(parse(Float64, x)))))
"(¬1.0) → 0.0"
```

!!! note
    For any `Formula` type `F`, this function should be the inverse of [`syntaxstring`](@ref); that is, if `φ::F` then the following should hold, for at least some `args`, and for every `kwargs` allowing correct parsing: `φ == parseformula(F, syntaxstring(φ, args...; kwargs...), args...; kwargs...)`.


See also [`SyntaxTree`](@ref), [`BASE_PARSABLE_CONNECTIVES`](@ref), [`syntaxstring`](@ref).
