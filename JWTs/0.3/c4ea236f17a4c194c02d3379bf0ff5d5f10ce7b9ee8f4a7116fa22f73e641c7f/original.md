```
sign!(jwt, key, kid)
```

Sign the JWT using the key. The key id and key algorithm is included in the JWT header. Updates the jwt with the header and signature. Returns `nothing`.

Arguments:

  * `jwt`: The JWT to sign. If the JWT is already signed, it is not signed again.
  * `key`: The JWK to use for signing.
  * `kid`: The key id to include in the JWT header.
