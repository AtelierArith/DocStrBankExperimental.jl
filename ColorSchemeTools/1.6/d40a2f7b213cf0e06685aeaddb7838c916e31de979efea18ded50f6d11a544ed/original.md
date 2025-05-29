```
add_alpha(cs::ColorScheme, f::Function)
```

Make a copy of the colorscheme `cs` with alpha opacity values defined by the function.

### Example

Make a copy of the PuOr colorscheme, set the opacity of each element to be the result of calling the function on the value. So at value 0.5, the opacity is 1.0, but it's 0.0 at either end.

```julia
add_alpha(ColorSchemes.PuOr, (n) -> sin(n * π))
```
