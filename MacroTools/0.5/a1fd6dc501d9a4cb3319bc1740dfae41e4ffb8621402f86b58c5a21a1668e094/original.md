```
rmlines(x)
```

Remove the line nodes from a block or array of expressions.

Compare `quote end` vs `rmlines(quote end)`

### Examples

To work with nested blocks:

```julia
prewalk(rmlines, ex)
```

See also: [`@q`](@ref)
