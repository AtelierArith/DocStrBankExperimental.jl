```
street(n::Integer = 1; kws...)
street(options::Vector{<:AbstractString}, n::Integer; kws...)
street(mask::Vector{<:AbstractString}; kws...)
```

`n` のストリート名を生成します。オプションおよびマスクベースの生成の場合、提供できる有効なオプションは `country_code` のみです。

# パラメータ

  * `n::Integer = 1`: 生成するストリート名のエントリ数。
  * `options::Vector{<:AbstractString}`: 生成される可能性のある値を制限するオプションを含むベクター。
  * `mask::Vector{<:AbstractString}`: 要素ごとのオプション制限を持つマスクベクター。
