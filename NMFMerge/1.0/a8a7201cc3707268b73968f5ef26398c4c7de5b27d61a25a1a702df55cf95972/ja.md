```
Wnormalized, Hnormalized = colnormalize(W, H, p=2)
```

因子分解を正規化して、各列が `||W[:, i]||_p ≈ 1` を満たすようにします。
