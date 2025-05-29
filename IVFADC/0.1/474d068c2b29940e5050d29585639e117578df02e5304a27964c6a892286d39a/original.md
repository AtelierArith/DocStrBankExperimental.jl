```
knn_search(ivfadc, point, k[; w=1])
```

Searches at most `k` closest neighbors of `point` in the index `ivfadc`; the neighbors will be searched for in the points contained in the closest `w` clusters.
