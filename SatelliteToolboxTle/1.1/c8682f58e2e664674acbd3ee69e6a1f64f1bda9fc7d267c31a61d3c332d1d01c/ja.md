```
fetch_tles(fetcher::T; kwargs...) -> Vector{TLE}
```

`fetcher`を使用してTLEを取得します。

キーワード`kwargs...`は検索をカスタマイズするために使用されます。これはフェッチャーのタイプ`T`に依存します。
