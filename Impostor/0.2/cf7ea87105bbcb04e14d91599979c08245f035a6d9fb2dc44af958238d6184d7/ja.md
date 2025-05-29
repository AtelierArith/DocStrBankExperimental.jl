```
university(n::Integer = 1; kws...)
university(fields::Vector{<:AbstractString}, n::Integer; kws...)
university(field_mask::Vector{<:AbstractString}; kws...)
```

# パラメータ

  * `n::Integer = 1`: 生成する大学エントリの数。
  * `options::Vector{<:AbstractString}`: 生成される可能な値を制限するオプションを含むベクター。
  * `mask::Vector{<:AbstractString}`: 要素ごとのオプション制限を持つマスクベクター。

# オプション

`options` と `mask` の要素に対する有効なオプション値は次のとおりです：

  * `"business"`
  * `"humanities"`
  * `"social-sciences"`
  * `"natural-sciences"`
  * `"formal-sciences"`
  * `"public-administration"`
  * `"military"`

# Kwargs

  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale` が提供されていない場合、現在のセッションのロケールが使用されます。
