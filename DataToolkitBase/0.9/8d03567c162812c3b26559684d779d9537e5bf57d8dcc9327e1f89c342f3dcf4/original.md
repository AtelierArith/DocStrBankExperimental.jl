```
storage(storer::DataStorage, as::Type; write::Bool=false)
```

Fetch a `storer` in form `as`, appropiate for reading from or writing to (depending on `write`).

By default, this just calls `getstorage` or `putstorage` (when `write=true`).

This executes this component of the overall data flow:

```
Storage ◀────▶ Data
```
