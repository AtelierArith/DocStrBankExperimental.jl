```
encode(sp, payload)
```

Encode each 254-byte block in the `payload` and directly send  the data through a specified serial port, `sp`. This is faster than first encoding the whole payload and then seding it.
