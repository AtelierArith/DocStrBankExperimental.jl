```
gsblkdiag(A, E, B, C; smarg, disc = false, fast = true, finite_infinite = false, stable_unstable = false, trinv = false, 
          atol1 = 0, atol2 = 0, rtol, withQ = true, withZ = true) -> (At, Et, Bt, Ct, Q, Z, ν, blkdims, sep)
```

通常の行列ペンシル `A - λE` を、変換行列 `Q` と `Z` を使用して、同等のブロック対角三角形形式 `At - λEt = Q*(A - λE)*Z` に還元します。変換された行列 `At` と `Et` は、安定性マージンパラメータ `smarg` と安定性タイプパラメータ `disc` に関して、無限、安定、非安定の固有値が分離されている必要があります。`disc = false` の場合、`Cs` は実部が `smarg` より小さい複素数の集合であり、`disc = true` の場合、`Cs` は絶対値が `smarg` より小さい複素数の集合（すなわち、原点を中心とした半径 `smarg` の円の内部）です。`smarg = missing` の場合、デフォルト値は `smarg = 0`（`disc = false` の場合）または `smarg = 1`（`disc = true` の場合）です。

ペンシル `At - λEt` は、次のいずれかのブロック上三角形形式になります。

(1) `finite_infinite = false` の場合、

```
               | Ai-λEi   *      0    |
    At - λEt = |    O   A1-λE1   0    |
               |    0     0    A2-λE2 |
```

ここで、`ni x ni` サブペンシル `Ai-λEi` は無限の基本因子を含み、`n1 x n1` サブペンシル `A1-λE1` は一般化シュール形式のペア `(A1,E1)` を持ち、`n2 x n2` サブペンシル `A2-λE2` は一般化シュール形式のペア `(A2,E2)` を持ちます。ペンシル `A1-λE1` は非安定な有限固有値を持ち、`A2-λE2` は安定な有限固有値を持つ場合、`stable_unstable = false` であり、`A1-λE1` は安定な有限固有値を持ち、`A2-λE2` は非安定な有限固有値を持つ場合、`stable_unstable = true` です。

サブペンシル `Ai-λEi` は階段形式であり、`Ai` は非特異で上三角形、`Ei` は nilpotent で上三角形です。`nb` 次元のベクトル `ν` は、階段形式 `Ai-λEi` の対角ブロックの次元を含み、`i` 番目のブロックは次元 `ν[i] x ν[i]` を持ちます。`ν[i]-ν[i+1]` の差は、`i = 1, 2, ..., nb` の場合、次数 `i` の無限基本因子の数です（`ν[nb+1] = 0`）。

対角ブロックの次元は `blkdims = (ni, n1, n2)` で返されます。

(2) `finite_infinite = true` の場合、

```
               | A1-λE1   0      0    |
    At - λEt = |    O   A2-λE2   *    |
               |    0     0    Ai-λEi |
```

ここで、`ni x ni` サブペンシル `Ai-λEi` は無限の基本因子を含み、`n1 x n1` サブペンシル `A1-λE1` は一般化シュール形式のペア `(A1,E1)` を持ち、`n2 x n2` サブペンシル `A2-λE2` は一般化シュール形式のペア `(A2,E2)` を持ちます。ペンシル `A1-λE1` は非安定な有限固有値を持ち、`A2-λE2` は安定な有限固有値を持つ場合、`stable_unstable = false` であり、`A1-λE1` は安定な有限固有値を持ち、`A2-λE2` は非安定な有限固有値を持つ場合、`stable_unstable = true` です。

サブペンシル `Ai-λEi` は階段形式であり、`Ai` は非特異で上三角形、`Ei` は nilpotent で上三角形です。`nb` 次元のベクトル `ν` は、階段形式 `Ai-λEi` の対角ブロックの次元を含み、`i` 番目のブロックは次元 `ν[i] x ν[i]` を持ちます。`ν[nb-j+1]-ν[nb-j]` の差は、`j = 1, 2, ..., nb` の場合、次数 `j` の無限基本因子の数です（`ν[0] = 0`）。

対角ブロックの次元は `blkdims = (n1, n2, ni)` で返されます。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ、`A` の非ゼロ要素の絶対許容誤差、`E` の非ゼロ要素の絶対許容誤差、`A` および `E` の非ゼロ要素の相対許容誤差を指定します。

還元は、`fast = true` の場合は列ピボットを伴うランクを明らかにするQR分解に基づくランク決定を使用して、または `fast = false` の場合はより信頼性の高いSVD分解を使用して行われます。

`withQ = true` の場合、`Q` は左変換行列を含み、`trinv = false` の場合はその逆行列、`trinv = true` の場合はその逆行列を含みます。`withQ = false` の場合、`Q` は `nothing` に設定されます。`withZ = true` の場合、`Z` は左変換行列を含み、`trinv = false` の場合はその逆行列、`trinv = true` の場合はその逆行列を含みます。`withZ = false` の場合、`Z` は `nothing` に設定されます。

`Bt = Q*B` ですが、`B = missing` の場合は `Bt = missing` が返され、`Ct = C*Z` ですが、`C = missing` の場合は `Ct = missing` が返されます。

2つの基礎となる対角ブロックのスペクトルの分離の推定値は `sep` で返され、`0 ≤ sep ≤ 1` です。値 `sep ≈ 0` は、`A1-λE1` と `A2-λE2` がほぼ等しい固有値を持つことを示します。 ```
