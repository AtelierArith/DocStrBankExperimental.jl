```
t8_cmesh_tree_to_face_encode(dimension, face, orientation)
```

与えられた面と面接続の向きの値に基づいて、ツリーから面への情報を計算します。

# 引数

  * `dimension`:[in] 対応するeクラスの次元。
  * `face`:[in] 面番号
  * `orientation`:[in] 面対面の向き。

# 戻り値

面/向きの組み合わせに対応するツリーから面へのエントリ。これは t8*eclass*max*num*faces[dimension] * orientation + face として計算されます。

### プロトタイプ

```c
int8_t t8_cmesh_tree_to_face_encode (const int dimension, const t8_locidx_t face, const int orientation);
```
