```
complete_name(n::Integer = 1; kws...)
complete_name(options::Vector{<:AbstractString}, n::Integer; kws...)
complete_name(mask::Vector{<:AbstractString}; kws...)
```

指定されたロケールから `n` または `length(mask)` の完全な名前を生成します。

# パラメータ

  * `n::Integer = 1`: 生成する完全な名前の数。

# オプション

`options` と `mask` の有効なオプション値は次のとおりです：

  * `"M"` は "男性" を表します
  * `"F"` は "女性" を表します

# キーワード引数

  * `locale::Vector{String}`: エントリがサンプリングされるロケール。`locale` が提供されていない場合、現在のセッションのロケールが使用されます。
  * `max_surnames::Integer = 3`: 生成される各エントリの姓の最大数。実際の数は `max_surnames` よりも少ない場合があります。

# 例

```@juliarepl
julia> Impostor.complete_name(["F"], 5)
5-element Vector{String}:
"Melissa Sheffard"
"Kate Collins"
"Melissa Cornell Fraser"
"Abgail Cornell"
"Abgail Fraser Jameson"

julia> complete_name(["F", "M", "F", "F", "M"])
5-element Vector{String}:
"Melissa Sheffard Jameson Cornell"
"Alfred Collins"
"Mary Sheffard Fraser"
"Milly Jameson Fraser"
"Alfred Fraser Collins"
```
