```
zlims!(low, high)
zlims!(; low = nothing, high = nothing)
```

現在の軸のz軸の制限を`low`と`high`に設定します。制限が高-低の順序である場合、これにより軸の向きが逆になります。制限が`nothing`に設定されている場合、軸内のプロットから自動的に決定されます。
