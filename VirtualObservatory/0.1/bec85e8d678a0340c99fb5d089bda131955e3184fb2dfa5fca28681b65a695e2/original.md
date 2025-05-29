```
TAPService(baseurl, [format="VOTABLE/TD"])
TAPService(service::Symbol)
```

Handler of a service following the Virtual Observatory Table Access Protocol (TAP), as [defined](https://www.ivoa.net/documents/TAP/) by IVOA. Instances of `TAPService` can be created by passing either a base URL of the service or a symbol corresponding to a known service: `:cadc`, `:gaia`, `:ned`, `:simbad`, `:vizier`.

A `TAPService` aims to follow the `DBInterface` interface, with query execution as the main feature: `execute(tap, query::String)`.

`TAPService` queries use `HTTP.request`. Keyword arguments for `HTTP.request` may be given in the `VirtualObservator.HTTP_REQUEST_OPTIONS` `Dict`. See the docstrings for `HTTP_REQUEST_OPTIONS` and `HTTP.request` for more details.
