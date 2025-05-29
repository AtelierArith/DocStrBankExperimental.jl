```julia
get(url::String) -> ::String
get(url::IP4) -> ::String
```

Performs a `GET` request from Julia.

```example
response = Toolips.get("https://github.com/ChifiSource")
```
