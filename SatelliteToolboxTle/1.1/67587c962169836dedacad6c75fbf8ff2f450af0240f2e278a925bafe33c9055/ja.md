```
create_tle_fetcher(::Type{CelestrakTleFetcher}; kwargs...) -> CelestrakTleFetcher
```

CelestrakサービスからTLEフェッチャーを作成します。

# キーワード

  * `url::String`: クエリを実行するために使用されるデフォルトのPHPウェブページアドレス。 (**デフォルト**: "https://celestrak.org/NORAD/elements/gp.php")
