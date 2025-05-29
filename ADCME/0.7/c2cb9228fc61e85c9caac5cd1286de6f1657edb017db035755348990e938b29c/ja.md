```
spzero(m::Int64, n::Union{Missing, Int64}=missing)
```

サイズ $m\times n$ の空の疎行列を構築します。`n` が `missing` の場合、`n=m` になります。
