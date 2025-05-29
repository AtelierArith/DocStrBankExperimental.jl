```
@syntax_flatmap begin
  # Vector behave similar to nested for loops within @syntax_flatmap
  a = [1, 2, 3]
  b = [10, 20]
  @pure a + b
end
# [11, 21, 12, 22, 13, 23]
```

This is the standard monadic syntax which uses `map` for map*like and `flatmap` for flatmap*like. See `Monadic.@monadic` for more details.
