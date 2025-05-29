```
detect_libstdcxx_version(max_minor_version::Int=30)
```

現在実行中のJuliaプロセスを検査して、リンクされているlibstdc++のバージョンを特定します（もしあれば）。 `max_minor_version`は、検索が行われるGLIBCXXの3.4シリーズの最新バージョンです。
