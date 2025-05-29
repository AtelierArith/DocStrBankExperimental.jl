```
get_data(server, dataset, parameters, tmin, tmax; format="csv")
```

Get data and metadata from a HAPI `server` for a given `dataset` and `parameters` within a time range `[tmin, tmax]`.

Supported data formats: "csv", "binary", "json".
