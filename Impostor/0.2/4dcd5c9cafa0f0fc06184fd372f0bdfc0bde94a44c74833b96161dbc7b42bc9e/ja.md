```
bank_official_name(n::Integer = 1; kwargs...)
bank_official_name(options::Vector, n::Integer; level::Symbol, kwargs...)
bank_official_name(mask::Vector; level::Symbol, kwargs...)
```

# パラメータ

  * `n::Integer = 1`: 生成する公式銀行名エントリの数
  * `options::Vector{<:AbstractString}`: 生成される可能性のある値を制限するオプションを含むベクター。
  * `mask::Vector{<:AbstractString}`: 要素ごとのオプション制限を持つマスクベクター。

# Kwargs

  * `level::Symbol = :bank_code`: オプションベースまたはマスクベースの生成を使用する際の`options`または`mask`内の値のレベル。
  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale`が提供されていない場合、現在のセッションのロケールが使用されます。
