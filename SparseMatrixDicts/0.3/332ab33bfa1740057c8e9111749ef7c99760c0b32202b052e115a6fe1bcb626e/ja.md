```
merged_add!(A,B)
merged_add!(A,B, α=1.0)
merged_add!(A,B, α=1.0,β=1.0)
```

これは `A` を `αA + βB` で更新します（つまり、`A = αA + βB` を実行します）。デフォルトの (α,β) は (1.0,1.0) で、結果は `A + B` になります。
