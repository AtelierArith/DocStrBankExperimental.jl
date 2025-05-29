```
greedycliquing(A::AbstractMatrix{Bool},  minsize::Int)
greedycliquing!(A::AbstractMatrix{Bool},  minsize::Int)
```

貪欲クリークアルゴリズムは、次の基にしています: https://gitlab.invenia.ca/invenia/autopredictor/blob/develop/Tools/PreProcessing/GreedyCliquing.m

隣接行列をクリーク [1] と残りの非クリークノードに分割します。最適なクリークによる最大ノードセット削減を達成する以前のバージョンと比較して、このバージョンは最大クリークを見つけ、そのノードを隣接行列から削除し、クリークが見つからなくなるまで繰り返します。これに関する詳細は、この [2] Google ドキュメントで確認できます。

[1] http://en.wikipedia.org/wiki/Clique*(graph*theory) [2] https://docs.google.com/a/invenia.ca/document/d/1lLRfQT*TFJi1bTfIu*jGxDs1u9A9HYKX5s4Zta3VRNg/edit?usp=sharing

# 引数

  * `A::AbstractMatrix{Bool}`: 隣接行列
  * `minsize::Int`: 最小貪欲クリークサイズ

# 戻り値

  * `cliques::Array{Clique}`: クリーク型のベクトル配列
  * `singletons::Vector{Bool}`: Bool型のベクトル配列。これらはクリークに含まれないノードを示します

```
