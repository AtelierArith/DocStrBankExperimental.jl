```
verify_access_token!(j::Verifier, jwt::String)
```

Verify the given access token using the given Verifier. The Verifier must have been created with the same issuer as the access token. The access token must be a valid JWT and must have been issued by the same issuer as the Verifier. The access token must also be valid according to the claims*to*validate passed to the Verifier constructor.

Returns a Jwt object containing the claims of the access token.
