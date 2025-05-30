```
fuzzy_equal(M1::Matroid, M2::Matroid, reps::Int=1000)::Bool
```

これは、2つのマトロイドが等しいかどうかを確認するためのランダム化テストです。結果が `false` の場合、確実に等しくありません。結果が `true` の場合、おそらく等しいです。
