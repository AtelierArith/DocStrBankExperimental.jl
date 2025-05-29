Identical to [`FIELDS`](@ref) except that it includes the field types.

# Examples

The generated markdown text should look similar to to following example where a type has three fields; `x` of type `String`, `y` of type `Int`, and `z` of type `Vector{Any}`.

```markdown

  - `x::String`

  - `y::Int`: Unlike the `x` field this field has been documented.

  - `z::Array{Any, 1}`: Another documented field.
```
