```
prefix(n::Integer = 1; kws...)
prefix(options::Vector{String}, n::Integer; kws...)
prefix(mask::Vector{<:AbstractString}; kws...)
```

指定されたロケールから `n` 個の名前の接頭辞を生成します。*例*： `"Mr."` と `"Ms."`。

# パラメータ

  * `n::Integer = 1`: 生成する接頭辞の数。
  * `options::Vector{<:AbstractString}`: 生成される可能性のある値を制限するオプションを含むベクター。
  * `mask::Vector{<:AbstractString}`: 要素ごとのオプション制限を持つマスクベクター。

# オプション

`options` と `mask` の有効なオプション値は次のとおりです：

  * `"M"` は「男性」を表します。
  * `"F"` は「女性」を表します。

# Kwargs

  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale` が提供されていない場合、現在のセッションのロケールが使用されます。

# 例

```@juliarepl
julia> prefix(["F", "M", "F"])
3-element Vector{String}:
"Ms."
"Mr."
"Ms."
```
