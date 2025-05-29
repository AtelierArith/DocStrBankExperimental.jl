```
parsefeature(FT::Type{<:VarFeature}, expr::AbstractString; kwargs...)
```

Parse a [`VarFeature`](@ref) of type `FT` from its [`syntaxstring`](@ref) representation.

# Keyword Arguments

  * `featvaltype::Union{Nothing,Type} = nothing`: the feature's featvaltype   (recommended for some features, e.g., [`UnivariateFeature`](@ref));
  * `opening_parenthesis::String = "["`:   the string signaling the opening of an expression block (e.g., `"min[V2]"`);
  * `closing_parenthesis::String = "]"`:   the string signaling the closing of an expression block (e.g., `"min[V2]"`);
  * `additional_feature_aliases = Dict{String,Base.Callable}()`: A dictionary mapping strings to   callables, useful when parsing custom-made, non-standard features.   By default, features such as "avg" or "min" are provided for   (see `SoleData.BASE_FEATURE_FUNCTIONS_ALIASES`);   note that, in case of clashing `string`s,   the provided additional aliases will override the standard ones;
  * `variable_names_map::Union{Nothing,AbstractDict,AbstractVector} = nothing`:   mapping from variable name to variable index, useful when parsing from   `syntaxstring`s with variable names (e.g., `"min[Heart rate]"`);
  * `variable_name_prefix::String = "V"`:   prefix used with variable indices (e.g., "V10").

Note that at most one argument in `variable_names_map` and `variable_name_prefix` should be provided.

!!! note
    The default parentheses, here, differ from those of [`SoleLogics.parseformula`](@ref), since features are typically wrapped into `Atom`s, and `parseformula` does not allow parenthesis characters in atoms' `syntaxstring`s.


See also [`VarFeature`](@ref), [`featvaltype`](@ref), [`parsecondition`](@ref).
