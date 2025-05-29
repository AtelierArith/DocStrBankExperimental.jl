```
newickstring(hc::Hclust[, tiplabels::AbstractVector[<:String]])
```

convert Hclust to newick tree string

Args:

  * hc: `Hclust` object from Clustering package
  * tiplabels: `AbstractVector{<:String}` names in same order as distance matrix

Returns:

  * [newick tree](https://en.wikipedia.org/wiki/Newick_format) formated string
