```
xlims!(low, high)
xlims!(; low = nothing, high = nothing)
```

現在の軸のx軸の制限を`low`と`high`に設定します。制限が高-低の順に並んでいる場合、これにより軸の向きが反転します。`nothing`に設定された制限は、軸内のプロットから自動的に決定されます。
