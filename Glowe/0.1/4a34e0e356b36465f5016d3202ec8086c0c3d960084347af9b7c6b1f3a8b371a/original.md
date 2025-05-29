```
analogy(wv, pos, neg, n=5)
```

Compute the analogy similarity between two lists of words. The positions and the similarity values of the top `n` similar words will be returned. For example, `king - man + woman = queen` will be `pos=["king", "woman"], neg=["man"]`.
