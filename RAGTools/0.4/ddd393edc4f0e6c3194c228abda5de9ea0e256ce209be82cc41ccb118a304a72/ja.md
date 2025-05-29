```
get_tags(tagger::PassthroughTagger, docs::AbstractVector{<:AbstractString};
	tags::AbstractVector{<:AbstractVector{<:AbstractString}},
	kwargs...)
```

`tags`を文字列のベクトルのベクトルとして直接渡します（つまり、`tags[i]`は`docs[i]`のタグです）。その後、タグから語彙を構築し、タグを行列形式で返し、語彙も返します。
