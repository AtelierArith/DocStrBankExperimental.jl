```
validate!(jwt, keyset)
```

Validate the JWT using the keys in the keyset. The JWT must be signed. An exception is thrown otherwise. The keyset must contain the key id from the JWT header. A KeyError is thrown otherwise. The optional `algorithms` parameter can be used to specify the algorithms to use for validation.

Returns `true` if the JWT is valid, `false` otherwise.
