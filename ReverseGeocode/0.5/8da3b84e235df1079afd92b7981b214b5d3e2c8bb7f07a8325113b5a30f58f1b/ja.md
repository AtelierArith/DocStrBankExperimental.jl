```
decode(gc::Geocoder, point) => NamedTuple{(:country, :country_code, :city), Tuple{String, String, String}}
```

単一のポイントをデコードします。多くのポイントを処理する場合は、このメソッドをループで使用するのではなく、`decode(gc, points)`を使用することをお勧めします。
