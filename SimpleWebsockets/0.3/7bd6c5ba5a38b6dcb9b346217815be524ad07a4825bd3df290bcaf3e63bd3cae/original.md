```
ping(ws::WebsocketConnection, data::Union{String, Number})
```

Send `data` as ping message to the `ws` peer.

`data` is limited to 125Bytes, and will automatically be truncated if over this limit.
