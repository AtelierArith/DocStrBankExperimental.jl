```
with_valid_jwt(f, jwt, keyset; kid=nothing)
```

Run `f` with a valid JWT. The validated JWT is passed as an argument to `f`. If the JWT is invalid, an `ArgumentError` is thrown.

Arguments:

  * `f`: The function to execute with a valid JWT. The validated JWT is passed as an argument to `f`.
  * `jwt`: The JWT string or JWT object to use. If a string is passed, it is converted to a JWT object.
  * `keyset`: The JWKSet to use for validation. Only keys in this keyset are used for validation.

Keyword arguments:

  * `kid`: The key id to use for validation. If not specified, the `kid` from the JWT header is used.
  * `algorithms`: Ensure validation with one of the listed algorithms. Not enforced by deault.
