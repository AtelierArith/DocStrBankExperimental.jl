```
onehot([T=Float64], dit_str[; nbatch])
```

型 `Vector{T}` の onehot ベクトルまたは型 `Matrix{T}` の onehot ベクトルのバッチを作成します。ここで、インデックス `x + 1` が 1 になります。非ゼロエントリの値は、ペアを入力することで指定できます。
