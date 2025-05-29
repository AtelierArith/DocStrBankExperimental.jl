```
@syntax_map begin
  # Vectors behave similar to nested for loops within @syntax_map
  a = [1, 2, 3]
  b = [10, 20]
  @pure a + b
end
# [[11, 21], [12, 22], [13, 23]]
```

This is a variant of the monadic syntax which uses `map` for both map*like and flatmap*like. See `Monadic.@monadic` for more details.
