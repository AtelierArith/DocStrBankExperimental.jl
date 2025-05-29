```
add_alpha(cs::ColorScheme, alpha::Vector)
```

Make a copy of the colorscheme `cs` with alpha opacity values in the vector `alpha`.

### Example

Make a copy of the PuOr colorscheme, set the first element to have alpha opacity 1.0, the last element to have opacity 0.0, with intermediate elements taking values between 1.0 and 0.0.

```julia
add_alpha(ColorSchemes.PuOr, [1.0, 0.0])
```
