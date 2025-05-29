```
p8est_connectivity_face_neighbor_corner_set(c, f, nf, set)
```

隣接する面の1つを通じてコーナーを隣接木に変換します。事前に計算された面の置換インデックスを期待します。

### パラメータ

  * `c`:[in] 0..7の範囲のコーナー番号。
  * `f`:[in] コーナー *c* に接触する面番号。
  * `nf`:[in] 反対側にある隣接面。
  * `set`:[in] *f*、*nf*、および有効な向きを使用して取得される *p8est*face*permutation_sets* の値: ref = p8est*face*permutation*refs[f][nf]; set = p8est*face*permutation*sets[ref][orientation];

### 戻り値

他の面から見た0..7の範囲のコーナー番号。

### プロトタイプ

```c
int p8est_connectivity_face_neighbor_corner_set (int c, int f, int nf, int set);
```
