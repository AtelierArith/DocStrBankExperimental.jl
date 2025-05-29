```
derivative!(result, f, x, l, ::Val{P})
derivative!(result, f!, y, x, l, ::Val{P})
```

インプレース微分計算API。`result`は事前に割り当てられ、`y`と同じ形状であることが期待されます。
