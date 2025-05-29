```
add_alpha(cs::ColorScheme, alpha::Real=0.5)
```

Make a copy of the colorscheme `cs` with alpha opacity value `alpha`.

### Example

Make a copy of the PuOr colorscheme and set every element of it to have alpha opacity 0.5

```julia
add_alpha(ColorSchemes.PuOr, 0.5)
```
