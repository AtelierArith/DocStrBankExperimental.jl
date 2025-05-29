```
z, p, k = zpkdata(sys)
```

システム `sys` のゼロ、極、およびゲインを計算します。

### 戻り値

  * `z` : Matrix{Vector{ComplexF64}}, (ny × nu)
  * `p` : Matrix{Vector{ComplexF64}}, (ny × nu)
  * `k` : Matrix{Float64}, (ny × nu)
