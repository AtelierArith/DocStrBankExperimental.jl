```
geturl(provider::Provider, x::Integer, y::Integer, z::Integer)
```

Replace `x`, `y` and `z` in the provider url.

If the provider options have keys other than `:max_zoom` and `:attribution` they will also be replaced.

We follow the behaviour of Leaflet.js so their provider urls work without modification in `Provider`.
