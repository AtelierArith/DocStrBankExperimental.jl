```
QGramSortedVector(s, q::Integer = 2)
```

An iterator with a pre-computed sorted vector of its qgrams. This enables faster calculation of QGram  distances.

Since qgrams are sorted in lexicographic order QGram distances can be  calculated even faster than when using a QGramDict. However, the  sorting means that updating the counts after creation is less  efficient. However, for most use cases QGramSortedVector is preferred over a QgramDict.

Note that the qgram length must correspond with the q length used in the distance.

## Examples

```julia
str1, str2 = "my string", "another string"
qs1 = QGramSortedVector(str1, 2)
qs2 = QGramSortedVector(str2, 2)
evaluate(Jaccard(2), qs1, qs2)
```
