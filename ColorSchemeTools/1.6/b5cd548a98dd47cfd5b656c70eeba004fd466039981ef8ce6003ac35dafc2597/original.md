```
add_alpha(cs::ColorScheme, r::Range)
```

Make a copy of the colorscheme `cs` with alpha opacity values in the range `r`.

### Example

Make a copy of the PuOr colorscheme, set the first element to have alpha opacity 0.5, the last element to have opacity 0.0, with intermediate elements taking values between 0.5 and 1.0.

```julia
add_alpha(ColorSchemes.PuOr, 0.5:0.1:1.0)
```
