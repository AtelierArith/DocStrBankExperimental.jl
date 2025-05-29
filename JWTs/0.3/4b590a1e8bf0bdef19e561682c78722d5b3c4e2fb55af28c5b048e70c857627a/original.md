```
sign!(jwt, keyset, kid)
```

Sign the JWT using the keys in the keyset. The key id and key algorithm is included in the JWT header. Updates the jwt with the header and signature. Returns `nothing`.

Arguments:

  * `jwt`: The JWT to sign. If the JWT is already signed, it is not signed again.
  * `keyset`: The JWKSet to use for signing. Only keys in this keyset are used for signing.
  * `kid`: The key id to use for signing. The keyset must contain the key id from the JWT header. A KeyError is thrown otherwise.
