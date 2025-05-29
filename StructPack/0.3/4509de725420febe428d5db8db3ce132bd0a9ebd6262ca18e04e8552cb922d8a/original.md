```
step(io::IO)
```

Enter or skip the msgpack value in `io`.

If the value is in map or vector format, step into it. Otherwise, skip the element.

Returns the core format of the value skipped or stepped into.

For example, if a msgpack array is stored in `io`, then `step(io); unpack(io)` will (generically) unpack the first element of the array.
