```
getblock(blockname::String; api::AbstractPrefectConfig = PrefectAPI())
```

Makes an `HTTP.get()` call to provided URL endpoint, default endpoint constructed by `PrefectAPI`. Returns a Dict containing the Prefect Block specification.
