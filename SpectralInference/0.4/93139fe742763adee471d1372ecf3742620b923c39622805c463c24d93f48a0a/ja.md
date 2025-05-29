```
newickstring(hc::Hclust[, tiplabels::AbstractVector[<:String]])
```

Hclustをnewickツリー文字列に変換します

引数:

  * hc: クラスタリングパッケージからの`Hclust`オブジェクト
  * tiplabels: 距離行列と同じ順序の`AbstractVector{<:String}`名

戻り値:

  * [newickツリー](https://en.wikipedia.org/wiki/Newick_format)形式の文字列

```
