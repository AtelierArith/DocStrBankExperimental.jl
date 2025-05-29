```
weighted_reservoir_sample_without_replacement(rng, iter, wv, n; ordered = false, method = :alg_AExpJ)
```

重み付きリザーバサンプリングアルゴリズム（置換なし）。`method`キーワードは、`:alg_ARes`または`:alg_AExpJ`のいずれかにすることができます。`wv`は、イテレータの要素を受け取り、`Float64`を返す関数である必要があります。

「重み付きランダムサンプリングとリザーバ、P. S. Efraimidis et al., 2006」で説明されているアルゴリズムA-ResおよびA-ExpJから適応されました。
