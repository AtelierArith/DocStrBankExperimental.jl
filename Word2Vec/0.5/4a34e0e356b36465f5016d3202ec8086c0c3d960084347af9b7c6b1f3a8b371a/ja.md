```
analogy(wv, pos, neg, n=5)
```

2つの単語リスト間の類似性を計算します。上位 `n` の類似単語の位置と類似性の値が返されます。例えば、`king - man + woman = queen` は `pos=["king", "woman"], neg=["man"]` になります。
