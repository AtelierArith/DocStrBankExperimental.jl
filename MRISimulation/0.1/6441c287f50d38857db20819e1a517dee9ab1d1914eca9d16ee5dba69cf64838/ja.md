```
epgDephasing(F::Vector{T}, n=1) where T = circshift(F[:],n)
```

は、n個の脱相サイクルに対応する横脱相状態 `F` をシフトします。
