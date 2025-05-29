```julia
GUE <: ContinuousMatrixDistribution
GUE(n)
```

  * `n` : 次元
  * **ガウス単位エンセmbles**（`GUE`）は、上三角のエントリが分布 $N(0,1)_{\mathbf{C}}$ に従う独立同分布（iid）であり、対角エントリが分布 $N(0,1)_{\mathbf{R}}$ に従う独立同分布（iid）であり、上三角のものとは独立な $n \times n$ エルミート行列 $M_{n}$ のエンセmblesです。

```julia
rand(M::GUE, norm::bool) 
```

  * `norm` : デフォルトは `false` で、`norm` が `true` に設定されている場合、行列は $\operatorname{min}(n,m)^{-1/2}$ で正規化されます。

# 例

GUE(3) から 3×3 のランダム行列を生成します。

```julia
rand(GUE(3))

3×3 Hermitian{ComplexF64, Matrix{ComplexF64}}:
 -0.883413+0.0im         1.09872+0.874884im     -0.1985-1.04778im
   1.09872-0.874884im    1.55483+0.0im        -0.488532+1.18694im
   -0.1985+1.04778im   -0.488532-1.18694im   -0.0823873+0.0im
```

```julia
rand(GUE(2),norm=true)
2×2 Hermitian{ComplexF64, Matrix{ComplexF64}}:
 -0.457089+0.0im       -0.672713-0.102234im
 -0.672713+0.102234im   0.380126+0.0im
```
