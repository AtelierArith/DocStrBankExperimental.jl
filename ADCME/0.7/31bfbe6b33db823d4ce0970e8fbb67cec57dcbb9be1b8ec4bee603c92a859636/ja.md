```
spdiag(n::Int64)
```

サイズ $n\times n$ のスパース単位行列を構築します。これは `spdiag(n, 0=>ones(n))` と同等です。
