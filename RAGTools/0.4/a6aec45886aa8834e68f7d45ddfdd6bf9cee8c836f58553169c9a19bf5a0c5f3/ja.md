```
setpropertynested(nt::NamedTuple, parent_keys::Vector{Symbol},
	key::Symbol,
	value
```

)

ネストされたNamedTuple `nt`のプロパティ`key`のセッターで、プロパティは`parent_keys`のキーにネストされています。

親キーのサブセット内のプロパティを変更したい場合に便利です（例：`retriever_kwargs`内の`model`）。

# 例

```julia
kw = (; abc = (; def = "x"))
setpropertynested(kw, [:abc], :def, "y")
# 出力: (abc = (def = "y",),)
```

パイプライン内のCHATベースのステップで全ての`model`キーを変更する実用的な例：

```julia
# 親キーが以下のリストにある場合、:modelを"gpt4t"に変更します（チャットベースのステップ）
setpropertynested(kwargs,
	[:rephraser_kwargs, :tagger_kwargs, :answerer_kwargs, :refiner_kwargs],
	:model, "gpt4t")
```

または、埋め込みモデルを変更する（インデクサーとリトリーバーの両方のステップで、同じステップ名のため）：

```julia
kwargs = setpropertynested(
		kwargs, [:embedder_kwargs],
		:model, "text-embedding-3-large"
	)
```
