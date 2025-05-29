```
p4est_find_face_transform(connectivity, itree, iface, ftransform)
```

ツリー隣接変換の軸の組み合わせで配列を埋めます。

### パラメータ

  * `itree`:[in] 元のツリーの番号。
  * `iface`:[in] 元のツリーの面の番号。
  * `ftransform`:[out] この配列は9つの整数を保持します。[0,2] 元の面の座標軸の順序。[3,5] 対象面の座標軸の順序。[6,8] 軸tのエッジ逆転フラグ; 軸nの面コード。[1,4,7] 0（3Dとの互換性のために未使用）。

### 戻り値

隣接する面のツリーが存在する場合、その番号を返し、存在しない場合は-1を返します。

### プロトタイプ

```c
p4est_topidx_t p4est_find_face_transform (p4est_connectivity_t * connectivity, p4est_topidx_t itree, int iface, int ftransform[]);
```
