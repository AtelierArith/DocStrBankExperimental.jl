```
firstname(n::Integer = 1; kws...)
firstname(sexes::Vector{<:AbstractString}, n::Integer; kws...)
firstname(sexes::Vector{<:AbstractString}; kws...))
```

`n` または `length(mask)` のファーストネームを生成します。

# パラメータ

  * `n::Integer = 1`: 生成するファーストネームの数。
  * `options::Vector{<:AbstractString}`: 生成される可能な値を制限するオプションを含むベクター。
  * `mask::Vector{<:AbstractString}`: 要素ごとのオプション制限を持つマスクベクター。

# オプション

`options` と `mask` の有効なオプション値は次のとおりです：

  * `"M"` は "男性" を表します。
  * `"F"` は "女性" を表します。

# キーワード引数

  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale` が提供されない場合、現在のセッションのロケールが使用されます。

# 例

```@juliarepl
julia> firstname(["F"], 4)
4-element Vector{String}:
"Sophie"
"Abgail"
"Sophie"
"Mary"

julia> firstname(["F", "M", "F", "F", "M"])
5-element Vector{String}:
"Sophie"
"Carl"
"Milly"
"Amanda"
"John"
```
