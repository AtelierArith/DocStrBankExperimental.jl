```
surname(n::Integer = 1; kws...)
```

提供された `locale` をソースとして `surname` を生成します。

# パラメータ

  * `n::Integer = 1`: 生成する姓の数。

# キーワード引数

  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale` が提供されていない場合は、現在のセッションのロケールが使用されます。
