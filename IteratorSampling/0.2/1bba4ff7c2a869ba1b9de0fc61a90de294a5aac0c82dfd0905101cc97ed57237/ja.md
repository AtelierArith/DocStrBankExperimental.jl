```
weighted_reservoir_sample_with_replacement(rng, iter, wv, n; ordered = false)
```

重み付きリザーバサンプリングアルゴリズム（置換あり）。`wv` はイテレータの要素を受け取り、`Float64` を返す関数である必要があります。

「A Skip-based Algorithm for Weighted Reservoir Sampling with Replacement, A. Meligrana, 2024」で説明されているアルゴリズム WRSWR_SKIP から適応されています。
