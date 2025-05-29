```
zlims!(ax, low, high)
zlims!(ax; low = nothing, high = nothing)
zlims!(ax, zlims)
```

軸 `ax` の z 軸の制限を `low` と `high` に設定するか、タプル `zlims = (low,high)` に設定します。制限が高-低の順序である場合、軸の向きは反転します。制限が `nothing` の場合、軸内のプロットから自動的に決定されます。
