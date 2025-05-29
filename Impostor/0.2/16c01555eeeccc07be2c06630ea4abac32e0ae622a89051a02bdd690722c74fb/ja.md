```
bank_name(n::Integer = 1; kwargs...)
bank_name(options::Vector, n::Integer; level::Symbol, kwargs...)
bank_name(mask::Vector; level::Symbol, kwargs...)
```

# パラメータ

  * `n::Integer = 1`: 生成する銀行名エントリの数
  * `options::Vector{<:AbstractString}`: 生成される可能性のある値を制限するオプションを含むベクター。
  * `mask::Vector{<:AbstractString}`: 要素ごとのオプション制限を持つマスクベクター。

# Kwargs

  * `level::Symbol = :bank_code`: オプションベースまたはマスクベースの生成を使用する際の`options`または`mask`内の値のレベル。
  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale`が提供されていない場合、現在のセッションのロケールが使用されます。

# 例

```@repl
julia> bank_name(5; locale = ["pt_BR"])
5-element Vector{String}:
 "Broker"
 "Nubank"
 "Itaubank"
 "Renascenca"
 "Daycoval"
```
