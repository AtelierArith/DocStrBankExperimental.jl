```
t8_element_face_neighbor_inside(ts, elem, neigh, face, neigh_face)
```

与えられた要素の面隣接要素を構築します。この面隣接要素がルートツリー内にある場合は、その要素を返します。そうでない場合は0を返します。

# 引数

  * `ts`:[in] クラススキームの実装。
  * `elem`:[in] 考慮すべき要素。
  * `neigh`:[in,out] *face* に沿った *elem* の面隣接要素がルートツリー内にある場合、この要素のデータは面隣接要素のデータで埋められます。そうでない場合、データは任意に変更できます。
  * `face`:[in] 隣接要素を構築するための面の番号。
  * `neigh_face`:[out] *neigh* から見た *face* の番号。隣接要素がルートツリー内にない場合は任意の値。

# 戻り値

*neigh* がルートツリー内にある場合は真。そうでない場合は偽。この場合、出力時の *neigh* のデータは任意です。

### プロトタイプ

```c
int t8_element_face_neighbor_inside (const t8_eclass_scheme_c *ts, const t8_element_t *elem, t8_element_t *neigh, int face, int *neigh_face);
```
