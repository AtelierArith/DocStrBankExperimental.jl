```
URI(; scheme="", host="", port="", etc...)
URI(str) = parse(URI, str::String)
```

A type representing a URI (e.g. a URL). Can be constructed from distinct parts using the various supported keyword arguments, or from a string. The `URI` constructors will automatically escape any provided `query` arguments, typically provided as `"key"=>"value"::Pair` or `Dict("key"=>"value")`. For all other components, you need to manually percent encode them before passing them to the `URI` constructor. Note that multiple values for a single query key can provided like `Dict("key"=>["value1", "value2"])`, in which case the constructor will percent encode *only* the values you pass in as the `query` part.

When constructing a `URI` from a `String`, you need to ensure that the string is correctly percent encoded already.

The `URI` struct stores the complete URI in the `uri::String` field and the component parts in the following `SubString` fields:

  * `scheme`, e.g. `"http"` or `"https"`
  * `userinfo`, e.g. `"username:password"`
  * `host` e.g. `"julialang.org"`
  * `port` e.g. `"80"` or `""`
  * `path` e.g `"/"`
  * `query` e.g. `"Foo=1&Bar=2"`
  * `fragment`

The `queryparams(::URI)` function returns a `Dict` containing the `query`.

Note that you manually need to percent decode the content of the individual component fields before you further use their content, as they are returned in percent-encoded form.
