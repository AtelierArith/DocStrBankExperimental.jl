```julia
randSymmetric(d, n; Diag, norm) 

randSymmetric(n; norm)
```

  * `d` : エントリ分布
  * `n` : 次元
  * `norm` : デフォルト `false`、`norm` が `true` に設定されている場合、行列は $n^{-1/2}$ で正規化されます。
  * `diag` : デフォルト `diag = d`、対角エントリの分布。対角要素に異なる分布（例えば二項分布）を使用するには、`diag = Binomial(1,0.5)` と設定します。
  * 参照: [`GOE`](@ref)

# 例

標準ガウス分布からのエントリを持つ 3×3 のランダム対称行列を生成します。

```julia
randSymmetric(3)

3×3 Symmetric{Float64, Matrix{Float64}}:
 -0.230698  -1.72846     0.306362
 -1.72846    0.0845915  -0.0116108
  0.306362  -0.0116108  -0.559046
```
