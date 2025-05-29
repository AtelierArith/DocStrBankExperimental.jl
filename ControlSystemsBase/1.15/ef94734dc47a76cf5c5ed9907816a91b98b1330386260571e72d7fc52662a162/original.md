```
z, p, k = zpkdata(sys)
```

Compute the zeros, poles, and gains of system `sys`.

### Returns

  * `z` : Matrix{Vector{ComplexF64}}, (ny × nu)
  * `p` : Matrix{Vector{ComplexF64}}, (ny × nu)
  * `k` : Matrix{Float64}, (ny × nu)
