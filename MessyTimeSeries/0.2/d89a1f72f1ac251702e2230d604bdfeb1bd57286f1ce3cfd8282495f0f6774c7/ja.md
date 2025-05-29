```
rand_without_replacement(rng::StableRNGs.LehmerRNG, n::Int64, T::Int64, d::Int64)
```

位置ベクトル `P` から `length(P)-d` 要素を重複なしで抽出します。

サンプリングプロセスでは、各時点で n-1 要素を超えて削除されることはありません。プロセスの中で `P` は永続的に変更されます。
