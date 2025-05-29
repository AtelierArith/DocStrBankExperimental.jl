```
function normalize_psi(ψ::Matrix{Float64})::Matrix{Float64}
```

行列 `Ψ` を正規化して、最小値がゼロ、指定されたプラズマ境界で 1.0 になるようにします。

正規化された行列を返します。
