```
spdiag(o::PyObject)
```

スパース対角行列を構築します。対角成分は `o` であり、これは `spdiag(length(o), 0=>o)` と同等です。
