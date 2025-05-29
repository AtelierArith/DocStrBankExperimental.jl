```
data(handle::Message)
```

Retrieve the longitudes, latitudes, and values from the message.

# Example

```
GribFile(filename) do f
    msg = Message(f)
    lons, lats, values = data(msg)
end
```
