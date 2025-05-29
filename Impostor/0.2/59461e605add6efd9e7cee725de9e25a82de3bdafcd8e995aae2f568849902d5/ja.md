```
highschool(n::Integer = 1; kwargs...)
```

# パラメータ

  * `n::Integer = 1`: 生成する高校名の数。

# Kwargs

  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale`が提供されていない場合は、現在のセッションのロケールが使用されます。
