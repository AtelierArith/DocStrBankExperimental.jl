```
QGram(q::Int)
```

Creates a QGram distance.

The distance corresponds to

$||v(s1, q) - v(s2, q)||$

where $v(s, q)$ denotes the vector on the space of q-grams of length q,  that contains the number of times a q-gram appears for the string s
