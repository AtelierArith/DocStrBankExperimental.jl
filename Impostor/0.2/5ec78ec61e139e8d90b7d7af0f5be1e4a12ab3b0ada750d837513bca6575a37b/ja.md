```
nationality(n::Integer = 1; kws...)
nationality(options::Vector{<:AbstractString}, n::Integer; level::Symbol, kws...)
nationality(mask::Vector{<:AbstractString}; level::Symbol, kws...)
```

# パラメータ

  * `n::Integer = 1`: 生成する国籍エントリの数。
  * `options::Vector{<:AbstractString}`: 生成される可能性のある値を制限するオプションを含むベクター。
  * `mask::Vector{<:AbstractString}`: 要素ごとのオプション制限を持つマスクベクター。

# キーワード引数

  * `level::Symbol = :district_name`: オプションベースまたはマスクベースの生成を使用する際の `options` または `mask` の値のレベル。 有効な `level` 値は次のとおりです：

      * `:sex`
      * `:country_code`
  * `locale::Vector{String}`: エントリがサンプリングされるロケール。 `locale` が提供されていない場合、現在のセッションのロケールが使用されます。
