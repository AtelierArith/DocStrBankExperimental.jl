```julia
trytoken(
    tks::ExtendableGrids.TokenStream,
    expected::String
) -> Bool

```

Try for keyword token.

It token is missing, the token read is put back into stream, a value of false is returned and the next try/gettoken command continues at the same position,

Otherwise, true is returned, and reading continues after the token found.
