```
Asset(url)
Asset(name, url)
Asset(name => url)
Asset(filetype, name, url)
```

A browser asset that can be loaded by WebIO.

The `url` parameter may be either a remote URL or a local filepath (which will be served via AssetRegistry.jl). All of the following are valid `url` values.

  * `https://unpkg.com/react@16/umd/react.development.js`
  * `//unpkg.com/react@16/umd/react.development.js`
  * `./path/to/foo.js`

By default, the filetype is guessed as the extension of the specified url (only `"js"`, `"css"`, and `"html"` are currently supported) but may be specified if nonstandard extensions are in use.
