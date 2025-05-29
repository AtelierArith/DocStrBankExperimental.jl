```
y = cumtrapz(Δt, x)
```

ファントムの各スピンに対する時間に沿った台形累積積分。

# 引数

  * `Δt`: (`1 x NΔt ::Matrix{Float64}`, `[s]`) デルタ時間の1行配列
  * `x`: (`Ns x (NΔt+1) ::Matrix{Float64}`, `[T]`) フィールドの大きさ Gx * x + Gy * y + Gz * z

# 戻り値

  * `y`: (`Ns x NΔt ::Matrix{Float64}`, `[T*s]`) 各列がファントムの各スピンに対する (Gx * x + Gy * y + Gz * z) * Δt の時間に沿った累積積分である行列
