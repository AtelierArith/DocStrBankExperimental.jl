```
save(writer::Datasaveer{driver}, destination::Any, information::Any)
```

Using a certain `writer`, save the `information` to the `destination`.

This fulfils this component of the overall data flow:

```
Data          Information
  ▲               ╷
  ╰────writer─────╯
```
