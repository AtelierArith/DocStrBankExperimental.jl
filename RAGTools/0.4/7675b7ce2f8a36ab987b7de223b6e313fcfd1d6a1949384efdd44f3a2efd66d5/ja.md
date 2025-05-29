```
find_closest(
	finder::BinaryCosineSimilarity, emb::AbstractMatrix{<:Bool},
	query_emb::AbstractVector{<:Real}, query_tokens::AbstractVector{<:AbstractString} = String[];
	top_k::Int = 100, rescore_multiplier::Int = 4, minimum_similarity::AbstractFloat = -1.0, kwargs...)
```

クエリ埋め込み（`query_emb`）に最も近いチャンクのインデックス（`emb`内の埋め込みで表される）を、バイナリ埋め込み（インデックス内）を使用して見つけます。

これは二段階のアプローチです：

  * 第一段階：バイナリ形式のハミング距離を使用して、`top_k * rescore_multiplier`（つまり、top_kより多くの）候補を取得します。
  * 第二段階：浮動小数点埋め込みで候補を再スコアリングし、top_kを返します。

最も近いインデックスは`top_k`のみを返します。

参考文献: [HuggingFace: Embedding Quantization](https://huggingface.co/blog/embedding-quantization#binary-quantization-in-vector-databases)。

# 例

任意の浮動小数点埋め込みを次のようにバイナリに変換します：

```julia
binary_emb = map(>(0), emb)
```
