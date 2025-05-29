```julia
GOE <: ContinuousMatrixDistribution
GOE(n) 
```

  * `n` : 次元
  * **ガウス直交アンサンブル**（`GOE`）は、上三角のエントリが分布 $N(0,1)_{\mathbf{R}}$ に従う独立同分布（iid）の $n \times n$ 対称行列 $M_{n}$ のアンサンブルであり、対角エントリは分布 $N(0,2)_{\mathbf{R}}$ に従い、上三角のエントリとは独立である。

```julia
rand(M::GOE, norm::bool)
```

  * `norm` : デフォルトは `false`。`norm` を `true` に設定すると、行列は $\operatorname{min}(n,m)^{-1/2}$ で正規化されます。

# 例

GOE(3) から 3×3 のランダム行列を生成する

```julia
rand(GOE(3))

3×3 Symmetric{Float64, Matrix{Float64}}:
 -1.62391   -0.451433    0.863883
 -0.451433   0.0271799  -0.524854
  0.863883  -0.524854   -0.00930624
```

```julia
rand(GOE(3),norm=true)

3×3 Symmetric{Float64, Matrix{Float64}}:
  0.302141   0.152634   -0.711679
  0.152634  -0.0629327   0.103075
 -0.711679   0.103075    1.51861
```
