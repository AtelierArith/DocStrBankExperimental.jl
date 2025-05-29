```
postcode(n::Integer = 1; kws...)
```

# パラメータ

  * `n::Integer = 1`: 生成する郵便番号の数。

# キーワード引数

  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale`が提供されていない場合、現在のセッションのロケールが使用されます。
