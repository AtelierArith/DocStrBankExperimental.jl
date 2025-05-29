```
CachedDataset(source, cachesize = numbobs(source))
CachedDataset(source, cacheidx = 1:numbobs(source))
CachedDataset(source, cacheidx, cache)
```

`source` データコンテナをラップし、`cachesize` サンプルをメモリにキャッシュします。これは、`source` が遅延データコンテナである場合に読み取り速度を向上させるのに役立ちますが、システムメモリがそれを大きなチャンクとして保存するのに十分な場合に限ります。

デフォルトでは、観測インデックス `1:cachesize` がキャッシュされます。手動で `cacheidx` のセットを渡すこともできます。

`source` のデフォルトキャッシュ作成をカスタマイズするには、[`make_cache`](@ref) も参照してください。
