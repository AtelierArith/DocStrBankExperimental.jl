```
ShowProps(o, props=propertynames(o);
          show_keywords=true, new_lines=false, keyword_style=Style(), entry_style=Style()
          separator=(new_lines ? Print(" = ") : Print("=")),
          kw...)
```

Show the properties of an object `o` via [`ShowList`](@ref) with entries using `ShowKw`.

## Arguments

  * `props`: Symbols with names of properties to show.
  * `show_keywords`: whether or not to show the property names.
  * `keyword_style::Style`: a style to apply to the keywords.
  * `entry_style::Style`: style to apply to entries.
  * `separator`: Separator to use between keyword and property.  By default, spacing will be added if `new_lines`.
  * `kw`: other keywords passed to [`ShowList`](@ref)

## Examples

```
julia> propertynames(1.0 + im)
(:re, :im)

julia> ShowProps(1.0 + im)
(re=1.0, im=1.0)

julia> ShowProps(1.0 + im, [:re])
(re=1.0)

julia> ShowProps(1.0 + im, [:re], keyword_style=Style(:red), new_lines=true)
(
    re = 1.0
)

julia> ShowProps(1.0 + im, show_keywords=false)
(1.0, 1.0)
```
