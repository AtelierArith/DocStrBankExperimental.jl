```
getpropertynested(
	nt::NamedTuple, parent_keys::Vector{Symbol}, key::Symbol, default = nothing)
```

ネストされた NamedTuple `nt` からプロパティ `key` を取得します。このプロパティは `parent_keys` のキーにネストされています。

ネストされた kwargs に便利で、`parent_keys` のサブセット内のプロパティを取得したい場合に使用します（例: `retriever_kwargs` の `model`）。

# 例

```julia
kw = (; abc = (; def = "x"))
getpropertynested(kw, [:abc], :def)
# 出力: "x"
```
