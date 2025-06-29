```
klf_right_refineinf!(νi, M, N, Z, R; roff = 0, coff = 0, withZ = true)
```

分割された行列ペンシル `M - λN` を縮小します（`*` は関連しないサブペンシルを示します）

```
         [   *         *        *  ] roff
M - λN = [   0       Mi-λNi     *  ] ni
         [   0         0        *  ] rtrail
           coff       ni     ctrail
```

正則サブペンシル `Mi-λNi` を階段形式に変換し、`Mi` が非特異で `Ni` が nilpotent かつ上三角行列であるように、直交またはユニタリ変換行列 `Z1` を使用して、同等の形 `F - λG = (M - λN)*Z1` に縮小します。`Mi` は上三角行列に変換され、`Ni` の上三角性が保持されます。`Mi-λNi` には `nb` の対角ブロックがあり、`i` 番目の対角ブロックの次元は `νi[i] x νi[i]` であると仮定します。

実行された直交またはユニタリ変換は `Z` に蓄積されます（すなわち、`Z <- Z*Z1`）、`withZ = true` の場合。

行列 `R` は `R*Z1` で上書きされますが、`R = missing` の場合は上書きされません。
