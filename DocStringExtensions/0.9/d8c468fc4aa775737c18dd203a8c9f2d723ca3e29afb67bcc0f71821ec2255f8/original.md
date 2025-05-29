An [`Abbreviation`](@ref) to include the names of the fields of a type as well as any documentation that may be attached to the fields.

# Examples

The generated markdown text should look similar to to following example where a type has three fields (`x`, `y`, and `z`) and the last two have documentation attached.

```markdown

  - `x`

  - `y`

    Unlike the `x` field this field has been documented.

  - `z`

    Another documented field.
```
