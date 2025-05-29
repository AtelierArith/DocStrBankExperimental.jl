```
StringEncoder(stream, to, from=enc"UTF-8")
```

Returns a new write-only I/O stream, which converts any text in the encoding `from` written to it into text in the encoding `to` written to `stream`. Calling `close` on the returned object is necessary to complete the encoding (but it does not close `stream`).

`to` and `from` can be specified either as a string or as an `Encoding` object.
