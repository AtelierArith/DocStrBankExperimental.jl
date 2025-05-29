```julia
MultiCheckBox(options::Vector; [default::Vector], [orientation ∈ [:row, :column]], [select_all::Bool])
```

A group of checkboxes - the user can choose which of the `options` to return. The value returned via `@bind` is a list containing the currently checked items.

See also: [`MultiSelect`](@ref).

`options` can also be an array of pairs `key::Any => value::String`. The `key` is returned via `@bind`; the `value` is shown.

# Keyword arguments

  * `defaults` specifies which options should be checked initally.
  * `orientation` specifies whether the options should be arranged in `:row`'s `:column`'s.
  * `select_all` specifies whether or not to include a "Select All" checkbox.

# Examples

```julia
@bind snacks MultiCheckBox(["🥕", "🐟", "🍌"]))

if "🥕" ∈ snacks
    "Yum yum!"
end
```

```julia
@bind functions MultiCheckBox([sin, cos, tan])

[f(0.5) for f in functions]
```

```julia
@bind snacks MultiCheckBox(["🥕" => "🐰", "🐟" => "🐱", "🍌" => "🐵"]; default=["🥕", "🍌"])
```

```julia
@bind animals MultiCheckBox(["🐰", "🐱" , "🐵", "🐘", "🦝", "🐿️" , "🐝",  "🐪"]; orientation=:column, select_all=true)
```
