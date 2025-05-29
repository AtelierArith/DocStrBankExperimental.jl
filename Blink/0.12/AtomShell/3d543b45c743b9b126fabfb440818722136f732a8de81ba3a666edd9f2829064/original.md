```
shell(; debug=false)
```

Get the currently active [`Electron`](@ref) shell instance (or activate one if none exists yet).

NOTE: The `debug` keyword argument only takes effect if there is not an active `Electron` instance. If there *is* an active instance, this function returns that instance without regards to whether or not the `debug` flag matches.
