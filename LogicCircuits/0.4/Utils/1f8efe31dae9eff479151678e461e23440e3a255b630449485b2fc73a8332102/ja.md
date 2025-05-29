```
make_missing_mcar(d::DataFrame; keep_prob::Float64=0.8)
```

データフレームのコピーを返し、一部の特徴をMCARとして欠損させます。`keep_prob`は各特徴を保持する確率です。
