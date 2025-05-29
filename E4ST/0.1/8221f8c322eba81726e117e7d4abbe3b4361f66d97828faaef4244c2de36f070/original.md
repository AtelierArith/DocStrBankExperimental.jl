```
comparison(value, v) -> comp::Function
```

Returns the appropriate comparison function for `value` to be compared to each member of `v`.

```
comparison(value, ::Type) -> comp::Function
```

Returns the appropriate comparison function for `value` to be compared to the 2nd argument type.  Here are a few options:

  * comparison(f::Function, ::Type) -> f
  * comparison(s::String, ::Type{<:AbstractString}) -> ==(s)
