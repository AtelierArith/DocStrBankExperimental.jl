```
QGramDict(s, q::Integer = 2)
```

An iterator with a pre-computed dictionary of its qgrams. This enables faster calculation of QGram  distances.

Note that the qgram length must correspond with the q length used in the distance.

## Examples

```julia
str1, str2 = "my string", "another string"
qd1 = QGramDict(str1, 2)
qd2 = QGramDict(str2, 2)
evaluate(Overlap(2), qd1, qd2)
```
