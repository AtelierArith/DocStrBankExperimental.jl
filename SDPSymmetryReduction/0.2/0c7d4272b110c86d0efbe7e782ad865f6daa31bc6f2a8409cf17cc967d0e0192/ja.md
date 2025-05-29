```
blockDiagonalize(P::Partition, verbose = true; epsilon = 1e-8, complex = false)
```

与えられた分割 `P` に基づいて (ジョルダン) 代数のブロック対角化をランダム化アルゴリズムを使用して決定します。`blockDiagonalize(P)` は、実際のブロック対角化 `blkd` を返します。存在しない場合は `nothing` を返します。

`blockDiagonalize(P; complex = true)` は同じものを返しますが、複素数値の行列を使用し、実際のブロック対角化が見つからなかった場合に使用する必要があります。複素数行列を実際に使用するには、エルミート行列 `A` が正半定値であるための条件は `[real(A) -imag(A); imag(A) real(A)]` が正半定値であることを思い出してください。

## 出力

  * `blkd.blkSizes` はブロックのサイズの整数配列です。
  * `blkd.blks` はサイズ `blkd.blkSizes` の (実数/複素数) 行列の配列を含む長さ `dim(P)` の配列です。すなわち、`blkd.blks[i]` は基底要素 `P.matrix .== i` の像です。
