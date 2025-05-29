```
intersection([f], g₁, g₂)
```

Compute the intersection of two geometries or domains `g₁` and `g₂` and apply function `f` to it. Default function is `identity`.

## Examples

```julia
intersection(g₁, g₂) do I
  if I isa CrossingLines
    # do something
  else
    # do nothing
  end
end
```

### Notes

When a custom function `f` is used that reduces the number of return types, Julia is able to optimize the branches of the code and generate specialized code. This is not the case when `f === identity`.
