```julia
randHankel(d, n;  norm )  

randHankel(n;  norm)
```

  * `d` : エントリ分布
  * `n` : 次元
  * `norm` : デフォルトは `false`。`norm` が `true` に設定されている場合、行列は $n^{-1/2}$ で正規化されます。

# 例

エントリが $\{1, i, \pi \}$ に一様分布する $5\times 5$ のランダムハンケル行列を生成します。

```julia
randHankel((1,im,pi),5)

5×5 Matrix{Number}:
  1   1  im  1   1
  1  im   1  1   π
 im   1   1  π   π
  1   1   π  π   π
  1   π   π  π  im
```
