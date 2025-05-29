```
address_complement(n::Integer = 1; kws...)
```

# パラメータ

  * `n::Integer = 1`: 生成するアドレス補完の数。

# キーワード引数

  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale`が提供されていない場合は、現在のセッションのロケールが使用されます。
