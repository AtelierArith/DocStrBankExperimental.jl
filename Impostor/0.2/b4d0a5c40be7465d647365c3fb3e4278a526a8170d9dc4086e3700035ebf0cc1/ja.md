```
country_code(n::Integer = 1; kws...)
country_code(options::Vector{<:AbstractString}, n::Integer; level::Symbol, kws...)
country_code(mask::Vector{<:AbstractString}; level::Symbol, kws...)
```

`n` または `length(mask)` の国コードを生成します。

# パラメータ

  * `n::Integer = 1`: 生成する国コードの数。
  * `options::Vector{<:AbstractString}`: 生成される可能性のある値を制限するオプションを含むベクター。
  * `mask::Vector{<:AbstractString}`: 要素ごとのオプション制限を持つマスクベクター。

# キーワード引数

  * `level::Symbol = :country_code`: オプションベースまたはマスクベースの生成を使用する際の `options` または `mask` の値のレベル。
  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale` が提供されていない場合、現在のセッションのロケールが使用されます。
