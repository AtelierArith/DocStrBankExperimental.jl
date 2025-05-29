```
country_official_name(n::Integer = 1; kws...)
country_official_name(options::Vector{<:AbstractString}, n::Integer; level::Symbol, kws...)
country_official_name(mask::Vector{<:AbstractString}; level::Symbol, kws...)
```

`n` または `length(mask)` の国の公式名を生成します。

# パラメータ

  * `n::Integer = 1`: 生成する国の公式名のエントリ数。
  * `options::Vector{<:AbstractString}`: 生成される可能性のある値を制限するオプションを含むベクター。
  * `mask::Vector{<:AbstractString}`: 要素ごとのオプション制限を持つマスクベクター。

# Kwargs

  * `level::Symbol = :country_code`: オプションベースまたはマスクベースの生成を使用する際の `options` または `mask` の値のレベル。
  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale` が提供されていない場合、現在のセッションのロケールが使用されます。
