```
get_vector(wv, word [; oov=false, oov_key="<unk>")
```

Returns the vector representation of `word` from the WordVectors `wv`. If `oov` is `true`, the vector corresponding to the key `oov_key` is returned for out-of-vocabulary words.
