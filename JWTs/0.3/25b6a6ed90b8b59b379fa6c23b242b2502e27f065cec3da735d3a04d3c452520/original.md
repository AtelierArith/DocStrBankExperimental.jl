```
kid(jwt::JWT)
```

Get the key id from the JWT header, or `nothing` if the `kid` parameter is not included in the JWT header.

The JWT must be signed. An exception is thrown otherwise.
