```
add_error(x, err)
```

Returns a copy of `x` with the absolute value of `err` added to the radius.

For complex `x` it adds the error to both the real and imaginary parts. For matrices it adds it elementwise.

See also [`setball`](@ref).
