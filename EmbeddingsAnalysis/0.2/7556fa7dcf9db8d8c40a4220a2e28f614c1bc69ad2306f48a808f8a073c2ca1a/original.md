```
cosine_vec(wv::WordVectors, wordvector, n=10 [;vocab=nothing])
```

Compute the cosine similarities and return best `n` positions and calculated values between `wordvector` and the word vectors from `wv`. A vocabulary mask `vocab` can be specified to consider only a subset of word vectors.
