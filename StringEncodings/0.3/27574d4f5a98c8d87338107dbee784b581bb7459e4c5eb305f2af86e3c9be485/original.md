```
StringDecoder(stream, from, to=enc"UTF-8")
```

Returns a new read-only I/O stream, which converts text in the encoding `from` read from `stream` into text in the encoding `to`.  Calling `close` on the stream does not close `stream`.

`to` and `from` can be specified either as a string or as an `Encoding` object.
