```
dropout!(B, A, p; [dims])
```

これは正確に `B .= dropout(A, p; dims)` を実行します。むしろ、これはアウトオブプレースの [`dropout`](@ref) の実装です。
