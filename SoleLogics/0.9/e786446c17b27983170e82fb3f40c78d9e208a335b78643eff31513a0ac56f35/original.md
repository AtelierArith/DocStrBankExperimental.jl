```
struct AnchoredFormula{L<:AbstractLogic} <: Formula
    _logic::Base.RefValue{L}
    synstruct::AbstractSyntaxStructure
end
```

A formula anchored to a logic of type `L`, and wrapping a syntax structure. The structure encodes a formula belonging to the grammar of the logic, and the truth of the formula can be evaluated on interpretations of the same logic. Note that, here, the logic is represented by a reference.

Upon construction, the logic can be passed either directly, or via a RefValue. Additionally, the following keyword arguments may be specified:

  * `check_atoms::Bool = false`: whether to perform or not a check that the atoms   belong to the alphabet of the logic;
  * `check_tree::Bool = false`: whether to perform or not a check that the formula's   syntactic structure honors the grammar   (includes the check performed with `check_atoms = true`);

*Cool feature*: a `AnchoredFormula` can be used for instating other formulas of the same logic. See the examples.

# Examples

```julia-repl
julia> φ = parsebaseformula("◊(p→q)");

julia> f2 = φ(parseformula("p"));

julia> syntaxstring(φ)
"◊(→(p, q))"

julia> syntaxstring(f2)
"p"

julia> @assert logic(φ) == logic(f2)

julia> @assert ◊ in operators(logic(f2))

julia> @assert ◊ isa operatorstype(logic(f2))

```

See also [`AbstractLogic`](@ref), [`logic`](@ref), [`SyntaxToken`](@ref), [`SyntaxBranch`](@ref), [`tree`](@ref).
