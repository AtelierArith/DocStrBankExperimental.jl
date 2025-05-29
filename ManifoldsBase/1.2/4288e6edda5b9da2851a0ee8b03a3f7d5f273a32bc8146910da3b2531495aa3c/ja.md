```
default_type(M::AbstractManifold, ft::FiberType)
```

マンフォールド `M` に基づくファイバーバンドルのファイバ `ft` からポイントのデフォルトタイプを取得します。例えば、`default_type(MyManifold(), TangentSpaceType())` を呼び出すと、接ベクトルのデフォルトタイプが得られます。
