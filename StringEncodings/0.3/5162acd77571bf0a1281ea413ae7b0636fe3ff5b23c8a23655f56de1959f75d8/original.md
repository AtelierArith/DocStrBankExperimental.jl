```
encodings()
```

List all encodings supported by `encode`, `decode`, `StringEncoder` and `StringDecoder` (i.e. by GNU libiconv).

Note that encodings typically appear several times under different names. In addition to the encodings returned by this function, the empty string (i.e. `""`) is equivalent to the encoding of the current locale.

Even more encodings may be supported: this can be checked by attempting a conversion.
