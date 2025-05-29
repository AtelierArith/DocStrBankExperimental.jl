```julia
expecttoken(
    tks::ExtendableGrids.TokenStream,
    expected::String
) -> Bool

```

Expect keyword token.

If token is missing, an UnexpectedTokenError is thrown If the token  has been found, reading will continue  at the position after the token found.
