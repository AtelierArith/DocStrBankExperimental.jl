```
p8est_find_face_transform(connectivity, itree, iface, ftransform)
```

隣接する面の変換の軸の組み合わせで配列を埋めます。

### パラメータ

  * `itree`:[in] 元の木の番号。
  * `iface`:[in] 元の木の面の番号。
  * `ftransform`:[out] この配列は9つの整数を保持します。[0]..[2] 元の面の座標軸の順序。[3]..[5] 対象面の座標軸の順序。[6]..[8] 軸t1、t2のエッジ反転フラグ; nの面コード。

### 戻り値

隣接する面の木が存在する場合はその木を、存在しない場合は-1を返します。

### プロトタイプ

```c
p4est_topidx_t p8est_find_face_transform (p8est_connectivity_t * connectivity, p4est_topidx_t itree, int iface, int ftransform[]);
```
