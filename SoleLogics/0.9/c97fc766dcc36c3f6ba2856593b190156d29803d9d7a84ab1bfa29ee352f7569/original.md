```
formulas(
    g::AbstractGrammar;
    maxdepth::Integer,
    nformulas::Union{Nothing,Integer} = nothing,
    args...
)::Vector{<:SyntaxBranch}
```

Enumerate the formulas produced by a given grammar with a finite and iterable alphabet.

# Implementation

Additional `args` can be used to model the function's behavior. At least these two arguments should be covered:

  * a `nformulas` argument can be used to limit the size of the returned `Vector`;
  * a `maxdepth` argument can be used to limit the syntactic component, represented as a syntax tree,

to a given maximum depth;

See also [`AbstractGrammar`](@ref), [`SyntaxBranch`](@ref).
