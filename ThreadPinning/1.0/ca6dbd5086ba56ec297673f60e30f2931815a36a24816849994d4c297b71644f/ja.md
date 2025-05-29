```
getnumanodes(; threadpool = :default)
```

現在実行中のJuliaスレッドに対応するCPUスレッドのNUMAノードのID（ゼロから始まる）を返します。

キーワード引数`threadpool`（デフォルト: `:default`）を使用すると、特定のスレッドプールに属するJuliaスレッドのみを考慮することができます。
