```
reservoir_sample_without_replacement(rng, iter, n; ordered = false, method = :alg_L)
```

置換なしのリザーバサンプリングアルゴリズム。`method`キーワードは`:alg_L`または`:alg_R`のいずれかにすることができます。

「リザーバを用いたランダムサンプリング、J. S. Vitter, 1985」で説明されているアルゴリズムRおよびLから適応されています。
