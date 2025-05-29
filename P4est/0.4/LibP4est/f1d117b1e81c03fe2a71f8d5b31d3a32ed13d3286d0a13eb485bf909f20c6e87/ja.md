```
p4est_expand_face_transform(iface, nface, ftransform)
```

隣接面変換の軸の組み合わせで配列を埋めます。

### パラメータ

  * `iface`:[in] 元の面の番号。
  * `nface`:[in] nface = r * 4 + nf としてエンコードされ、ここで nf = 0..3 は隣接面の接続面番号、r = 0..1 は隣接面に対する相対的な向きを示します。このエンコーディングは [`p4est_connectivity_t`](@ref) に一致します。
  * `ftransform`:[out] この配列は9つの整数を保持します。[0,2] 元の面の座標軸の順序で、最初は接線方向、2番目は法線方向を指します。(0, 1) の順列。[3,5] 対象面の座標軸の順序。[6,8] 接線軸のエッジ反転フラグ（ブール値）；法線座標 q の面コード [0, 3]: 0: q' = -q 1: q' = q + 1 2: q' = q - 1 3: q' = 2 - q [1,4,7] 0（3Dとの互換性のために未使用）。

### プロトタイプ

```c
void p4est_expand_face_transform (int iface, int nface, int ftransform[]);
```
