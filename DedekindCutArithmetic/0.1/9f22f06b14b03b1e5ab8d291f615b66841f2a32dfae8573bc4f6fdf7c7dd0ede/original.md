Parse a decimal literal into a Rational{BigInt}

```julia
julia> exact"0.1"
1//10
```

This is needed because literals are already parsed before constructing the AST, hence when writing :(x - 0.1) one would get the floating point approximation of 1//10 instead of the exact rational.
