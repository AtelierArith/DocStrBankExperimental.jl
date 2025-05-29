```
xlims!(ax, low, high)
xlims!(ax; low = nothing, high = nothing)
xlims!(ax, xlims)
```

軸 `ax` の x 軸の制限を `low` と `high` に設定するか、タプル `xlims = (low,high)` に設定します。制限が高-低の順序である場合、軸の向きは逆になります。制限が `nothing` の場合、軸内のプロットから自動的に決定されます。
