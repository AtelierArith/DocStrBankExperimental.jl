```
superscript(i::Rational; io::Union{IO, Nothing} = nothing)
```

Returns exponents as a string.

This function returns the value as a string. It does not print to `io`. `io` is only used for IO context values. If `io` contains the `:fancy_exponent` property and the value is a `Bool`, this value will override the behavior of fancy exponents.
