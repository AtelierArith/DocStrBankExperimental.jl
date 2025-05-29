```
fiblkdiag(A, E, B, C; fast = true, finite_infinite = false, trinv = false, atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) -> (At, Et, Bt, Ct, Q, Z, ν, blkdims, sep)
```

正則行列ペンシル `A - λE` を、変換行列 `Q` と `Z` を用いて、同等の形 `At - λEt = Q*(A - λE)*Z` に還元します。変換された行列 `At` と `Et` は、以下のいずれかのブロック対角形式になります。

(1) `finite_infinite = false` の場合、

```
               | Ai-λEi |   0     |
    At - λEt = |--------|---------|, 
               |    O   | Af-λEf  |
```

ここで、`ni x ni` サブペンシル `Ai-λEi` には無限の基本因子が含まれ、`nf x nf` サブペンシル `Af-λEf` には、ペンシル `A-λE` の有限固有値が含まれ、`Ef` は非特異かつ上三角です。

サブペンシル `Ai-λEi` は階段形式であり、`Ai` は非特異かつ上三角、`Ei` は nilpotent かつ上三角です。`nb` 次元のベクトル `ν` には、階段形式 `Ai-λEi` の対角ブロックの次元が含まれ、`i` 番目のブロックは次元 `ν[i] x ν[i]` を持ちます。`ν[i]-ν[i+1]` の差は、`i = 1, 2, ..., nb` の場合、次数 `i` の無限基本因子の数です（`ν[nb+1] = 0`）。

対角ブロックの次元は `blkdims = (ni, nf)` に返されます。

(2) `finite_infinite = true` の場合、

```
               | Af-λEf |   0    |
    At - λEt = |--------|--------|, 
               |   O    | Ai-λEi |
```

ここで、`nf x nf` サブペンシル `Af-λEf` には、ペンシル `A-λE` の有限固有値が含まれ、`Ef` は非特異かつ上三角です。また、`ni x ni` サブペンシル `Ai-λEi` には無限の基本因子が含まれます。

サブペンシル `Ai-λEi` は階段形式であり、`Ai` は非特異かつ上三角、`Ei` は nilpotent かつ上三角です。`nb` 次元のベクトル `ν` には、階段形式 `Ai-λEi` の対角ブロックの次元が含まれ、`i` 番目のブロックは次元 `ν[i] x ν[i]` を持ちます。`ν[nb-j+1]-ν[nb-j]` の差は、`j = 1, 2, ..., nb` の場合、次数 `j` の無限基本因子の数です（`ν[0] = 0`）。

対角ブロックの次元は `blkdims = (nf, ni)` に返されます。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ、`A` の非ゼロ要素の絶対許容誤差、`E` の非ゼロ要素の絶対許容誤差、および `A` と `E` の非ゼロ要素の相対許容誤差を指定します。

還元は、`fast = true` の場合は列ピボットを用いたランクを明らかにするQR分解に基づくランク決定を使用し、`fast = false` の場合はより信頼性の高いSVD分解を使用して行われます。

`withQ = true` の場合、`Q` には左変換行列が含まれ、`trinv = false` の場合はその逆行列が含まれます。`withQ = false` の場合、`Q` は `nothing` に設定されます。`withZ = true` の場合、`Z` には右変換行列が含まれ、`trinv = false` の場合はその逆行列が含まれます。`withZ = false` の場合、`Z` は `nothing` に設定されます。

`Bt = Q*B` ですが、`B = missing` の場合は `Bt = missing` が返され、`Ct = C*Z` ですが、`C = missing` の場合は `Ct = missing` が返されます。

`Ai-λEi` と `Af-λEf` のスペクトルの分離の推定値は `sep` に返され、`0 < sep ≤ 1` です。
