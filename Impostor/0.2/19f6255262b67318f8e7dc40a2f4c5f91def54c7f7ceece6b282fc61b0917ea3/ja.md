```
occupation(n::Integer = 1; kws...)
occupation(options::Vector{<:AbstractString}, n::Integer; kws...)
occupation(mask::Vector{<:AbstractString}; kws...)
```

`n` または `length(mask)` の職業エントリを生成します。

# パラメータ

  * `n::Integer = 1`: 生成する接頭辞の数。
  * `options::Vector{<:AbstractString}`: 生成される可能性のある値を制限するオプションを含むベクター。
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
