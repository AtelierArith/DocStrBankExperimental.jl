```
refresh!(keyset, keyseturl; default_algs)
refresh!(keyset; default_algs)
```

Arguments:

  * `keyset`: The JWKSet to refresh.
  * `keyseturl`: The URL to fetch the keys from.

Keyword arguments:

  * `default_algs`: A dictionary of default algorithms to use for each key type.

Refresh the keyset with the keys from the keyseturl. The keyseturl can either be of `http(s)://` or `file://` type. The keyset is updated with the keys from the keyseturl, old keys are removed.

If the keyseturl is not specified, the keyset is refreshed with the keys from the keyseturl already set in the keyset.

The default algorithm values are referred to only if the keyset does not specify the exact algorithm type. E.g. if only "RSA" is specified as the algorithm, "RS256" will be assumed.
