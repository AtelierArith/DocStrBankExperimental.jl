```
ssblkdiag(A, B, C; smarg, disc = false, stable_unstable = false, withQ = true, withZ = true) -> (At, Bt, Ct, Q, Z, blkdims, sep)
```

正則行列ペンシル `A - λI` を、変換行列 `Q` と `Z` を用いて、同等のブロック対角三角形形式 `At - λI = Q*(A - λI)*Z` に還元します。ここで `Q = inv(Z)` であり、変換された行列 `At` は、安定性マージンパラメータ `smarg` と安定性タイプパラメータ `disc` に関して、安定した固有値と不安定な固有値が分離されている必要があります。`disc = false` の場合、`Cs` は実部が `smarg` より小さい複素数の集合であり、`disc = true` の場合、`Cs` は絶対値が `smarg` より小さい複素数の集合（すなわち、原点を中心とした半径 `smarg` の円の内部）です。`smarg = missing` の場合、デフォルト値は `disc = false` の場合は `smarg = 0`、`disc = true` の場合は `smarg = 1` です。行列 `At` は次のブロック対角形式になります。

```
    At = | A1  0  |
         | 0   A2 |
```

ここで、`n1 x n1` 行列 `A1` と `n2 x n2` 行列 `A2` はシュール形式です。`stable_unstable = false` の場合、行列 `A1` は不安定な固有値を持ち、`A2` は安定な固有値を持ちます。一方、`stable_unstable = true` の場合、`A1` は安定な固有値を持ち、`A2` は不安定な固有値を持ちます。対角ブロックの次元は `blkdims = (n1, n2)` に返されます。`withQ = true` の場合、`Q` には左変換行列が含まれます。`withQ = false` の場合、`Q` は `nothing` に設定されます。`withZ = true` の場合、`Z` には右変換行列が含まれます。`withZ = false` の場合、`Z` は `nothing` に設定されます。`Bt = Q*B` ですが、`B = missing` の場合は `Bt = missing` が返され、`Ct = C*Z` ですが、`C = missing` の場合は `Ct = missing` が返されます。二つの基礎となる対角ブロックのスペクトルの分離の推定値は `sep` に返され、`0 ≤ sep ≤ 1` です。値 `sep ≈ 0` は `A1` と `A2` がほぼ等しい固有値を持つことを示します。
