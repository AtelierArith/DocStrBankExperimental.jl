```
    cosDocClose(doc::CosDoc)
```

Reclaims all system resources consumed by the `CosDoc`. The `CosDoc` should not be used after this method is called. `cosDocClose` only needs to be explicitly called if you have opened the document by 'cosDocOpen'. Documents opened with `pdDocOpen` do not need to use this method.
