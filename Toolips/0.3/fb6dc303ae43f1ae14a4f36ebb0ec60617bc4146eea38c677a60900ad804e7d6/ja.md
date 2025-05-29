```julia
get(url::String) -> ::String
get(url::IP4) -> ::String
```

Juliaから`GET`リクエストを実行します。

```example
response = Toolips.get("https://github.com/ChifiSource")
```
