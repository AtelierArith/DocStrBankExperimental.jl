```julia
randHermitian(d, n; diag, norm )

randHermitian(n; norm)
```

  * `d` : エントリ分布
  * `n`  : 次元
  * `norm` : デフォルトは `false`。`norm` を `true` に設定すると、行列は $n^{-1/2}$ で正規化されます。
  * `diag` : デフォルトは `diag = d`、対角エントリ分布。対角要素に異なる分布（例えば Circular(2)）を使用するには、`diag = Circular(2)` に設定します。対角エントリは常に虚部が `0` になるように強制されます。
  * 参照：[ `GUE`](@ref)

# 例

オフ対角エントリが標準複素ガウス分布、対角が標準正規分布の 2×2 のランダムエルミート行列を生成します。

```julia
randHermitian(2)

2×2 Hermitian{ComplexF64, Matrix{ComplexF64}}:
  0.382095+0.0im        -0.708469-0.0636734im
 -0.708469+0.0636734im   0.336952+0.0im
```

オフ対角エントリが [`Circular`](@ref)(1) で、対角エントリが一様に `-1` または `1` の 3×3 エルミート行列を生成します。

```julia
randHermitian(Circular(1),3,diag = (-1,1))

3×3 Hermitian{ComplexF64, Matrix{ComplexF64}}:
     1.0+0.0im       1.56259-0.676099im  1.39468-0.295073im
 1.56259+0.676099im     -1.0+0.0im       1.53369+0.296583im
 1.39468+0.295073im  1.53369-0.296583im     -1.0+0.0im
```

エントリが `Poisson(2)` のランダムな 2×2 対称行列を生成します。これは `randSymmetric(Poisson(2),3)` でも行うことができます。

```julia
randHermitian(Poisson(2),3)

3×3 Hermitian{Int64, Matrix{Int64}}:
 3  1  0
 1  1  2
 0  2  1
```

エントリが $\{1,2,3,...,10\}$ から一様に選ばれます。

```julia
randHermitian(1:10,2)

2×2 Hermitian{Int64, Matrix{Int64}}:
 10  7
  7  6
```

エントリが -1 または π で等しい確率で選ばれます。

```julia
randHermitian([-1,pi],3)

3×3 Hermitian{Float64, Matrix{Float64}}:
  3.14159  -1.0      -1.0
 -1.0      -1.0       3.14159
 -1.0       3.14159   3.14159
```
