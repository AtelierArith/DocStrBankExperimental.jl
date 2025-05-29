```
xcb_flush(conn:: XCBConnection) -> Bool
```

Forces any buffered output to be written to the server. Blocks until the write is complete. Returns `true` if the flush succeeds, or `false` otherwise.
