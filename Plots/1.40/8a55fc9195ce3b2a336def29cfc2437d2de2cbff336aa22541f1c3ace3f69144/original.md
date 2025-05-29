```
font(args...)
```

Create a Font from a list of features. Values may be specified either as arguments (which are distinguished by type/value) or as keyword arguments.

# Arguments

  * `family`: AbstractString. "serif" or "sans-serif" or "monospace"
  * `pointsize`: Integer. Size of font in points
  * `halign`: Symbol. Horizontal alignment (:hcenter, :left, or :right)
  * `valign`: Symbol. Vertical alignment (:vcenter, :top, or :bottom)
  * `rotation`: Real. Angle of rotation for text in degrees (use a non-integer type)
  * `color`: Colorant or Symbol

# Examples

```julia-repl
julia> font(8)
julia> font(family="serif", halign=:center, rotation=45.0)
```
