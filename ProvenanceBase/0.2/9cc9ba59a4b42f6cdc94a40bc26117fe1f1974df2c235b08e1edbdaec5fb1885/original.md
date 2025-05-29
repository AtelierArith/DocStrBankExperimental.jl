```
verify(object, provenance::Provenance) -> Bool
```

Check whether `provenance` was produced by `object`.

To be extended by packages that provide the required cryptographic methods. By default this function will work on `Provenance{NoSignature}` data, and will always verify successfully.
